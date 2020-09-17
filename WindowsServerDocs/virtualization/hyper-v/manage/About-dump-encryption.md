---
title: 关于转储加密
description: 介绍如何加密转储文件以及如何对加密进行故障排除。
ms.topic: article
ms.author: benarm
author: BenjaminArmstrong
ms.asset: b78ab493-e7c3-41f5-ab36-29397f086f32
ms.date: 11/03/2016
ms.openlocfilehash: d2258a810993ea903efe670355720a5fc65a888b
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746482"
---
# <a name="about-dump-encryption"></a>关于转储加密
转储加密可用于加密为系统生成的故障转储和实时转储。 转储使用为每个转储生成的对称加密密钥进行加密。 然后，使用由主机的受信任管理员指定的公钥对此密钥本身进行加密， (崩溃转储加密密钥保护程序) 。 这可确保只有具有匹配私钥的人员才能解密并因此访问转储的内容。 此功能在受保护的构造中得以利用。
注意：如果配置转储加密，还应禁用 Windows 错误报告。 WER 无法读取加密的故障转储。

## <a name="configuring-dump-encryption"></a>配置转储加密
### <a name="manual-configuration"></a>手动配置
若要使用注册表启用转储加密，请在下配置以下注册表值 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl`

| 值名称 | 类型 | 值 |
| ---------- | ---- | ----- |
| DumpEncryptionEnabled | DWORD | 1若要启用转储加密，请使用0禁用转储加密 |
| EncryptionCertificates\Certificate.1：:P ublicKey | 二进制 | 公钥 (RSA，2048位) 应用于加密转储。 这必须设置为 [BCRYPT_RSAKEY_BLOB](/windows/win32/api/bcrypt/ns-bcrypt-bcrypt_rsakey_blob)格式。 |
| EncryptionCertificates\Certificate.1：： Thumbprint | String | 允许在解密故障转储时自动查找本地证书存储中的私钥的证书指纹。 |


### <a name="configuration-using-script"></a>使用脚本进行配置
若要简化配置，可以使用 [示例脚本](https://github.com/Microsoft/Virtualization-Documentation/tree/live/hyperv-tools/DumpEncryption) 根据证书中的公钥启用转储加密。

1. 在受信任的环境中：创建包含2048位 RSA 密钥的证书并导出公共证书
2. 在目标主机上：将公共证书导入到本地证书存储
3. 运行示例配置脚本
    ```
    .\Set-DumpEncryptionConfiguration.ps1 -Certificate (Cert:\CurrentUser\My\093568AB328DF385544FAFD57EE53D73EFAAF519) -Force
    ```

## <a name="decrypting-encrypted-dumps"></a>解密加密转储
若要解密现有的加密转储文件，需要下载并安装适用于 Windows 的调试工具。 此工具集包含 KernelDumpDecrypt.exe 可用于解密加密的转储文件。
如果当前用户的证书存储中存在包含私钥的证书，则可以通过调用来解密转储文件

```
    KernelDumpDecrypt.exe memory.dmp memory_decr.dmp
```
解密后，WinDbg 之类的工具可以打开解密的转储文件。

## <a name="troubleshooting-dump-encryption"></a>转储加密故障排除
如果在系统上启用转储加密，但未生成转储，请检查系统 `System` 事件日志中是否有 `Kernel-IO` 事件1207。 当无法初始化转储加密时，将创建此事件并禁用转储。

| 详细错误消息 | 要缓解的步骤 |
| ---------------------- | ----------------- |
| 缺少公钥或指纹注册表 | 检查是否有两个注册表值存在于预期位置 |
| 公钥无效 | 请确保存储在 PublicKey 注册表值中的公钥存储为 [BCRYPT_RSAKEY_BLOB](/windows/win32/api/bcrypt/ns-bcrypt-bcrypt_rsakey_blob)。 |
| 不支持的公钥大小 | 目前仅支持2048位 RSA 密钥。 配置符合此要求的密钥 |

还要检查是否将下的值 `GuardedHost` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl\ForceDumpsDisabled` 设置为非0值。 这将完全禁用故障转储。 如果是这种情况，请将其设置为0。