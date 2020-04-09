---
title: manage-bde unlock
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7852bf7d-9102-40be-adcb-71e8f4dfde72
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e26952ca8c2b20cb0cb8efa167fca81e27b692a0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839733"
---
# <a name="manage-bde-unlock"></a>manage-bde：解除锁定



使用恢复密码或恢复密钥解锁受 BitLocker 保护的驱动器。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
manage-bde -unlock {-recoverypassword <Password>|-recoverykey <PathToExternalKeyFile>} <Drive> [-certificate {-cf PathToCertificateFile | -ct CertificateThumbprint} {-pin}] [-password] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|值|说明|
|---------|-----|-----------|
|-ms-fve-recoverypassword||指定将使用恢复密码来解锁驱动器。缩写：-rp|
||\<密码 >|表示可用于解锁驱动器的恢复密码。|
|-recoverykey||指定将使用外部恢复密钥文件来解锁驱动器。 缩写：-rk|
||\<PathToExternalKeyFile >|表示可用于解锁驱动器的外部恢复密钥文件。|
||\<驱动器 >|表示驱动器号后跟一个冒号。|
|-证书||要 unclock 卷的 BitLocker 证书的本地用户证书位于位置用户证书存储中。 缩写：-cert|
||< cf PathToCertificateFile >|证书文件的路径|
||<-ct CertificateThumbprint >|证书指纹，可以选择包含 PIN （-pin）。|
|-password||显示用于解锁卷的密码提示。 缩写：-pw|
|-computername||指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 缩写：-cn|
||\<名称 >|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?||在命令提示符下显示 brief Help。|
|-help 或-h||在命令提示符下显示完整的帮助。|

## <a name="examples"></a><a name=BKMK_Examples></a>示例

下面的示例演示如何使用 **-unlock**命令将 drive E 与已保存到另一驱动器上的备份文件夹的恢复密钥文件一起解锁。
```
manage-bde –unlock E: -recoverykey F:\Backupkeys\recoverykey.bek
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)