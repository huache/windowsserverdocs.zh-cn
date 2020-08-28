---
title: manage-bde unlock
description: Manage-bde 解锁命令的参考文章，可通过使用恢复密码或恢复密钥解锁受 BitLocker 保护的驱动器。
ms.topic: reference
ms.assetid: 7852bf7d-9102-40be-adcb-71e8f4dfde72
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e1d1566ee348b10efe2212c2e0004c72470944fe
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030095"
---
# <a name="manage-bde-unlock"></a>manage-bde unlock

使用恢复密码或恢复密钥解锁受 BitLocker 保护的驱动器。

## <a name="syntax"></a>语法

```
manage-bde -unlock {-recoverypassword <password>|-recoverykey <pathtoexternalkeyfile>} <drive> [-certificate {-cf pathtocertificatefile | -ct certificatethumbprint} {-pin}] [-password] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -ms-fve-recoverypassword | 指定将使用恢复密码来解锁驱动器。 你还可以使用 **-rp** 作为此命令的缩写形式。 |
| `<password>` | 表示可用于解锁驱动器的恢复密码。 |
| -recoverykey | 指定将使用外部恢复密钥文件来解锁驱动器。 你还可以使用 **-rk** 作为此命令的缩写形式。 |
| `<pathtoexternalkeyfile>` | 表示可用于解锁驱动器的外部恢复密钥文件。 |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -证书 | 用于解锁卷的 BitLocker 证书的本地用户证书位于本地用户证书存储中。 你还可以使用 **-cert** 作为此命令的缩写形式。 |
| -cf `<pathtocertificatefile>` | 证书文件的路径。 |
| -ct `<certificatethumbprint>` | 证书指纹，可以选择性地包括 PIN ( pin) 。 |
| -password | 显示用于解锁卷的密码提示。 你还可以使用 **-pw** 作为此命令的缩写形式。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要使用已保存到另一驱动器上的备份文件夹的恢复密钥文件来解锁 drive E，请键入：

```
manage-bde –unlock E: -recoverykey F:\Backupkeys\recoverykey.bek
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
