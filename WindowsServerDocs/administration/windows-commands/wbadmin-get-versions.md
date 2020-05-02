---
title: wbadmin get 版本
description: Wbadmin get 版本的参考主题，其中列出了存储在本地计算机或另一台计算机上的可用备份的详细信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b986acc4-d083-4d32-9434-862314ed5e97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 542f65b7d87eacb102f64fb4103e6c684df4faa5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720154"
---
# <a name="wbadmin-get-versions"></a>wbadmin get 版本



列出有关存储在本地计算机或另一台计算机上的可用备份的详细信息。 如果在没有参数的情况下使用此子命令，它将列出本地计算机的所有备份，即使这些备份不可用。 为备份提供的详细信息包括备份时间、备份存储位置、版本标识符（用于**wbadmin get items**子命令和执行恢复）以及可以执行的恢复类型。

若要使用此子命令获取有关可用备份的详细信息，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符**命令提示符**，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin get versions
[-backupTarget:{<BackupTargetLocation> | <NetworkSharePath>}]
[-machine:BackupMachineName]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|-backupTarget|指定包含您要了解其详细信息的备份的存储位置。 用于列出存储在该目标位置的备份。 备份目标位置可以是本地附加的磁盘驱动器、卷、远程共享文件夹、可移动媒体（如 DVD 驱动器或其他光学媒体）。 如果在创建备份的同一台计算机上运行**wbadmin get 版本**，则不需要此参数。 但是，若要获取有关从另一台计算机创建的备份的信息，需要使用此参数。|
|-计算机|指定您想要备份其详细信息的计算机。 当多台计算机的备份存储在同一位置时使用。 当指定 **-backupTarget**时，应使用。|

## <a name="remarks"></a>备注

若要列出可从特定备份中恢复的项，请使用**wbadmin get items**。

## <a name="examples"></a>示例

若要查看卷 h 上存储的可用备份的列表，请键入：
```
wbadmin get versions -backupTarget:h:
```
若要查看在计算机 server01 的远程共享文件夹\\ \\servername\share 中存储的可用备份的列表，请键入：
```
wbadmin get versions -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBBackupTarget](https://technet.microsoft.com/library/jj902447.aspx) cmdlet