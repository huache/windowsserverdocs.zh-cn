---
title: repair-bde
description: 有关 repair 命令的参考文章，可尝试重建严重损坏驱动器的关键部分，并在使用 BitLocker 对驱动器进行加密时抢救可恢复数据。
ms.topic: reference
ms.assetid: 534dca1a-05f7-4ea8-ac24-4fe5f14f988a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4caa619c248a30c48cdfc291f2fde25ba51d85f7
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766280"
---
# <a name="repair-bde"></a>repair-bde

如果驱动器已使用 BitLocker 加密，并且它具有有效的恢复密码或恢复密钥用于解密，则会尝试重建严重损坏的驱动器的关键部分，并抢救可恢复数据。

> [!IMPORTANT]
> 如果驱动器上的 BitLocker 元数据数据已损坏，则除了恢复密码或恢复密钥以外，还必须能够提供备份密钥包。 如果使用 Active Directory 域服务的默认密钥备份设置，则会在此处备份密钥包。 你可以使用 [bitlocker：使用 Bitlocker 恢复密码查看器](/windows/security/information-protection/bitlocker/bitlocker-use-bitlocker-recovery-password-viewer) 从 AD DS 获取密钥包。
>
> 使用密钥包以及恢复密码或恢复密钥，可以解密受 BitLocker 保护的驱动器的部分，即使磁盘已损坏。 每个密钥包仅适用于具有相应驱动器标识符的驱动器。

## <a name="syntax"></a>语法

```
repair-bde <inputvolume> <outputvolumeorimage> [-rk] [–rp] [-pw] [–kp] [–lf] [-f] [{-?|/?}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| `<inputvolume>` | 标识要修复的 BitLocker 加密驱动器的驱动器号。 驱动器号必须包含冒号;例如： **C：**。 如果未指定密钥包的路径，此命令将在驱动器中搜索密钥包。 如果硬盘驱动器损坏，此命令可能找不到包，并会提示你提供路径。 |
| `<outputvolumeorimage>` | 标识要在其上存储已修复驱动器的内容的驱动器。 输出驱动器上的所有信息都将被覆盖。 |
| -rk | 标识应用于解锁卷的恢复密钥的位置。 此命令还可以指定为 **-recoverykey**。 |
| -rp | 标识用于解锁卷的数字恢复密码。 此命令还可以指定为 **-ms-fve-recoverypassword**。 |
| -pw | 标识用于对卷进行解锁的密码。 此命令还可以指定为 **-password** |
| -kp | 标识可用于解锁卷的恢复密钥包。 此命令还可以指定为 **-ms-fve-keypackage**。 |
| -lf | 指定文件的路径，该文件将存储 Repair 错误、警告和信息消息。 此命令也可以指定为 **-logfile**。 |
| -f | 强制卸除卷，即使它无法锁定也是如此。 此命令还可以指定为 **-force**。 |
| -? 或 /? | 在命令提示符下显示帮助。 |

### <a name="limitations"></a>限制

此命令存在以下限制：

- 此命令无法修复在加密或解密过程中失败的驱动器。

- 此命令假设如果驱动器具有任何加密，则驱动器已完全加密。

## <a name="examples"></a>示例

若要尝试修复驱动器 C：，以将内容从驱动器 C：写入驱动器 D：使用恢复密钥文件 (在驱动器 F：上存储) ，并将此尝试的结果写入到驱动器 Z 上 ( # A0) ：，键入：

```
repair-bde C: D: -rk F:\RecoveryKey.bek –lf Z:\log.txt
```

若要尝试修复驱动器 C：并将内容从驱动器 C：写入驱动器 D：使用指定的48位数的恢复密码，请键入：

```
repair-bde C: D: -rp 111111-222222-333333-444444-555555-666666-777777-888888
```

>[!NOTE]
> 应在八个包含六个数字的块中键入恢复密码，并使用连字符分隔每个块。

若要强制驱动器 C：卸载，请尝试修复驱动器 C：，然后尝试修复驱动器 c：，然后将内容从驱动器 C：写入驱动器 D：使用恢复密钥包和恢复密钥文件 (在驱动器 F：上存储) ，键入：

```
repair-bde C: D: -kp F:\RecoveryKeyPackage -rk F:\RecoveryKey.bek -f
```

若要尝试修复驱动器 C：并将内容从驱动器 C：写入驱动器 D：，其中必须键入密码以解锁驱动器 C：在提示) 时 (，请键入：

```
repair-bde C: D: -pw
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)