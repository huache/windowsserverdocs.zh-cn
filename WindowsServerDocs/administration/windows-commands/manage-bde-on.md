---
title: manage-bde on
description: Manage-bde on 命令的参考主题，它对驱动器进行加密并打开 BitLocker。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f6a12814-df74-416c-a04a-62ea8512263e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bad56c9ade19d94fc5acc9b34a8cc42fe43b7c0d
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222859"
---
# <a name="manage-bde-on"></a>manage-bde on

加密驱动器并打开 BitLocker。

## <a name="syntax"></a>语法

```
manage-bde –on <drive> {[-recoverypassword <numericalpassword>]|[-recoverykey <pathtoexternaldirectory>]|[-startupkey <pathtoexternalkeydirectory>]|[-certificate]|
[-tpmandpin]|[-tpmandpinandstartupkey <pathtoexternalkeydirectory>]|[-tpmandstartupkey <pathtoexternalkeydirectory>]|[-password]|[-ADaccountorgroup <domain\account>]}
[-usedspaceonly][-encryptionmethod {aes128_diffuser|aes256_diffuser|aes128|aes256}] [-skiphardwaretest] [-discoveryvolumetype <filesystemtype>] [-forceencryptiontype <type>] [-removevolumeshadowcopies][-computername <name>]
[{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -ms-fve-recoverypassword | 添加数字密码保护程序。 你还可以使用 **-rp**作为此命令的缩写形式。 |
| `<numericalpassword>` | 表示恢复密码。 |
| -recoverykey | 添加用于恢复的外部密钥保护程序。 你还可以使用 **-rk**作为此命令的缩写形式。 |
| `<pathtoexternaldirectory>` | 表示恢复密钥的目录路径。 |
| -启动 | 添加用于启动的外部密钥保护程序。 你还可以使用 **-sk**作为此命令的缩写形式。 |
| `<pathtoexternalkeydirectory>` | 表示启动密钥的目录路径。 |
| -证书 | 为数据驱动器添加公钥保护程序。 你还可以使用 **-cert**作为此命令的缩写形式。 |
| -tpmandpin | 为操作系统驱动器添加受信任的平台模块（TPM）和个人标识号（PIN）保护程序。 你还可以使用 **-tp**作为此命令的缩写形式。 |
| -tpmandstartupkey | 添加操作系统驱动器的 TPM 和启动密钥保护程序。 你还可以使用 **-tsk**作为此命令的缩写形式。 |
| -tpmandpinandstartupkey | 为操作系统驱动器添加 TPM、PIN 和启动密钥保护程序。 你还可以使用 **-tpsk**作为此命令的缩写形式。 |
| -password | 添加数据驱动器的密码密钥保护程序。 你还可以使用 **-pw**作为此命令的缩写形式。 |
| -ADaccountorgroup | 为卷添加基于 SID 的标识保护程序。 如果用户或计算机具有正确的凭据，则该卷将自动解锁。 指定计算机帐户时，将附加 **$** 到计算机名称并指定 **– service** ，以指示应在 BitLocker 服务器的内容中而不是用户的情况下进行解锁。 你还可以使用 **-sid**作为此命令的缩写形式。 |
| -usedspaceonly | 将加密模式设置为仅加密已用空间。 包含已用空间的卷部分将被加密，但可用空间不会被加密。 如果未指定此选项，则卷上的所有已用空间和可用空间都将加密。 你还可以将**用作**此命令的缩写形式。 |
| -encryptionMethod | 配置加密算法和密钥大小。 你还可以使用 **-em**作为此命令的缩写形式。 |
| -skiphardwaretest | 开始加密而不进行硬件测试。 你还可以使用 **-s**作为此命令的缩写形式。 |
| -discoveryvolumetype | 指定要用于发现数据驱动器的文件系统。 发现数据驱动器是一个隐藏驱动器，添加到包含 BitLocker To Go 读取器的 FAT 格式 BitLocker 保护的可移动数据驱动器。 |
| -forceencryptiontype | 强制 BitLocker 使用软件或硬件加密。 可以将**硬件**或**软件**指定为加密类型。 如果选择了**硬件**参数，但驱动器不支持硬件加密，则 manage-bde 将返回错误。 如果组策略设置禁止指定的加密类型，则 manage-bde 将返回错误。 你还可以使用 **-fet**作为此命令的缩写形式。 |
| -removevolumeshadowcopies | 强制删除卷的卷影副本。 运行此命令后，你将无法使用以前的系统还原点还原此卷。 你还可以使用 **-rvsc**作为此命令的缩写形式。 |
| `<filesystemtype>` | 指定哪些文件系统可用于发现数据驱动器： FAT32、默认值或无。 |
| -computername | 指定正在使用 manage-bde 修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要打开驱动器 C 的 BitLocker 并将恢复密码添加到驱动器，请键入：

```
manage-bde –on C: -recoverypassword
```

若要打开驱动器 C 的 BitLocker，请将恢复密码添加到驱动器，并将恢复密钥保存到驱动器 E，请键入：

```
manage-bde –on C: -recoverykey E:\ -recoverypassword
```

若要打开驱动器 C 的 BitLocker，使用外部密钥保护程序（例如 USB 密钥）来解锁操作系统驱动器，请键入：

```
manage-bde -on C: -startupkey E:\
```

> [!IMPORTANT]
> 如果使用的是没有 TPM 的计算机，则此方法是必需的。

若要打开数据驱动器 E 的 BitLocker 并添加密码密钥保护程序，请键入：

```
manage-bde –on E: -pw
```

若要打开操作系统驱动器 C 的 BitLocker，并使用基于硬件的加密，请键入：

```
manage-bde –on C: -fet hardware
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde off 命令](manage-bde-off.md)

- [manage-bde pause 命令](manage-bde-pause.md)

- [manage-bde resume 命令](manage-bde-resume.md)

- [manage-bde 命令](manage-bde.md)
