---
title: wbadmin start systemstatebackup
description: 用于 wbadmin start systemstatebackup 的参考主题，该主题将创建本地计算机的系统状态备份，并将其存储在指定的位置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 998366c1-0a64-45e6-9ed3-4c3f5b8406f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5de3531f19312b9d0d7969a63639db6388487bc2
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821177"
---
# <a name="wbadmin-start-systemstatebackup"></a>wbadmin start systemstatebackup



创建本地计算机的系统状态备份，并将其存储在指定的位置。

> [!NOTE]
> Windows Server 备份不会作为系统状态备份或系统状态恢复的一部分备份或恢复注册表用户配置单元（HKEY_CURRENT_USER）。

若要使用此子命令执行系统状态备份，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin start systemstatebackup
-backupTarget:<VolumeName>
[-quiet]
```

### <a name="parameters"></a>参数

|   参数   |                                                                                                                                                                                                                      说明                                                                                                                                                                                                                      |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -backupTarget | 指定要存储备份的位置。 存储位置需要驱动器号或基于 GUID 的卷，格式为： \\ \\ ？ \Volume{*GUID*}。</br>在运行 Windows Server 2008 的计算机上不支持对共享网络文件夹进行系统状态备份。 如果你的服务器运行的是 Windows Server 2008 R2 或更高版本，则可以使用**backuptarget： \\ \\ servername\sharedFolder \\ **存储系统状态备份。 |
|    -quiet     |                                                                                                                                                                                                   对用户运行无提示的子命令。                                                                                                                                                                                                    |

## <a name="remarks"></a>备注

若要了解如何将系统状态备份保存到包含系统状态文件的卷，请参阅 Microsoft 知识库中的文章944530（ [https://go.microsoft.com/fwlink/?LinkId=110439](https://go.microsoft.com/fwlink/?LinkId=110439) ）。

## <a name="examples"></a>示例

若要创建系统状态备份并将其存储在卷 f 上，请键入：
```
wbadmin start systemstatebackup -backupTarget:f:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBBackup](https://technet.microsoft.com/library/jj902459.aspx) cmdlet