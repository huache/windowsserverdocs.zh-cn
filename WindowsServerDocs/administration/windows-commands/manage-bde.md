---
title: manage-bde
description: Manage-bde 命令的参考文章，用于打开或关闭 BitLocker，指定解锁机制，更新恢复方法，并解锁受 BitLocker 保护的数据驱动器。
ms.topic: article
ms.assetid: 276a7841-7289-48d4-a57d-bc7c300affbb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d1d910f9787d2a952a5e844c4aedb3d4c5ca53fa
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886568"
---
# <a name="manage-bde"></a>manage-bde

打开或关闭 BitLocker，指定解锁机制，更新恢复方法，并解锁受 BitLocker 保护的数据驱动器。

> [!NOTE]
> 此命令行工具可用于代替**BitLocker 驱动器加密**控制面板项。

## <a name="syntax"></a>语法

```
manage-bde [-status] [–on] [–off] [–pause] [–resume] [–lock] [–unlock] [–autounlock] [–protectors] [–tpm]
[–setidentifier] [-forcerecovery] [–changepassword] [–changepin] [–changekey] [-keypackage] [–upgrade] [-wipefreespace] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- |------------ |
| [manage-bde 状态](manage-bde-status.md) | 提供有关计算机上所有驱动器的信息，无论它们是否受 BitLocker 保护。 |
| [manage-bde on](manage-bde-on.md) | 加密驱动器并打开 BitLocker。 |
| [manage-bde off](manage-bde-off.md) | 解密驱动器并关闭 BitLocker。 解密完成后，将删除所有密钥保护程序。 |
| [manage-bde 暂停](manage-bde-pause.md) | 暂停加密或解密。 |
| [manage-bde 恢复](manage-bde-resume.md) | 恢复加密或解密。 |
| [manage-bde 锁](manage-bde-lock.md) | 阻止对受 BitLocker 保护的数据的访问。 |
| [manage-bde unlock](manage-bde-unlock.md) | 允许使用恢复密码或恢复密钥访问受 BitLocker 保护的数据。 |
| [manage-bde autounlock](manage-bde-autounlock.md) | 管理数据驱动器的自动解锁。 |
| [manage-bde 保护程序](manage-bde-protectors.md) | 管理加密密钥的保护方法。 |
| [manage-bde tpm](manage-bde-tpm.md) |  (TPM) 配置计算机的受信任的平台模块。 运行 Windows 8 或**win8_server_2**的计算机不支持此命令。 若要在这些计算机上管理 TPM，请使用 TPM 管理 MMC 管理单元或适用于 Windows PowerShell 的 TPM 管理 cmdlet。 |
| [manage-bde setidentifier](manage-bde-setidentifier.md)   | 将驱动器上的 "驱动器标识符" 字段设置为 "为**你的组织提供唯一标识符**组策略" 设置中指定的值。 |
| [manage-bde ForceRecovery](manage-bde-forcerecovery.md) | 重新启动时，强制 BitLocker 保护的驱动器进入恢复模式。 此命令从驱动器中删除所有与 TPM 相关的密钥保护程序。 计算机重新启动时，只能使用恢复密码或恢复密钥来解锁驱动器。 |
| [manage-bde changepassword](manage-bde-changepassword.md) | 修改数据驱动器的密码。 |
| [manage-bde changepin](manage-bde-changepin.md) | 修改操作系统驱动器的 PIN。 |
| [manage-bde changekey](manage-bde-changekey.md) | 修改操作系统驱动器的启动密钥。 |
| [manage-bde Ms-fve-keypackage](manage-bde-keypackage.md) | 为驱动器生成密钥包。 |
| [manage-bde 升级](manage-bde-upgrade.md) | 升级 BitLocker 版本。 |
| [manage-bde WipeFreeSpace](manage-bde-wipefreespace.md) | 擦除驱动器上的可用空间。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [使用命令行启用 BitLocker](/previous-versions/windows/it-pro/windows-7/dd894351(v=ws.10))
