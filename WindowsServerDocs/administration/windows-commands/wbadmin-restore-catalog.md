---
title: wbadmin restore catalog
description: 用于从指定存储位置为本地计算机恢复备份目录的 wbadmin restore catalog 参考文章。
ms.topic: reference
ms.assetid: ce1e24a0-821d-4353-b09d-8f82c5c4ad56
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46ebe9d8479ffe7b940cfe31c84176c3c1ef0aa9
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031925"
---
# <a name="wbadmin-restore-catalog"></a>wbadmin restore catalog

从指定的存储位置恢复本地计算机的备份目录。

若要使用此子命令恢复备份目录，您必须是 **Backup Operators** 组或 **Administrators** 组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行 **wbadmin** 。  (打开提升的命令提示符，右键单击 " **命令提示符**"，然后单击 "以 **管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

```
wbadmin restore catalog
-backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>}
[-machine:<BackupMachineName>]
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-backupTarget|指定在创建备份后的时间点的系统备份目录的位置。|
|-计算机|指定要恢复其备份目录的计算机的名称。 当多台计算机的备份存储在同一位置时使用。 当指定 **-backupTarget** 时，应使用。|
|-quiet|对用户运行无提示的子命令。|

## <a name="remarks"></a>注解

如果存储备份的位置 (磁盘、DVD 或远程共享文件夹) 已损坏或丢失，并且无法用于还原备份目录，请使用 **wbadmin delete catalog** 删除损坏的目录。 在这种情况下，你应在删除备份目录后创建新备份。

## <a name="examples"></a>示例

若要从磁盘 d：上存储的备份还原目录，请键入：
```
wbadmin restore catalog -backupTarget:d
```
若要从 servername\share 为 server01 的共享文件夹中存储的备份还原目录 \\ \\ ，请键入：
```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBCatalog](/powershell/module/windowserverbackup/?view=winserver2012r2-ps) cmdlet
