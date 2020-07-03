---
title: wbadmin start sysrecovery
description: Wbadmin start sysrecovery 参考文章，它使用指定的参数执行系统恢复（裸机恢复）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95b8232f-7c42-452b-838e-15b0cf6faebe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f7e23a82afba85ea8a670c636e0f700cb7def2e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930922"
---
# <a name="wbadmin-start-sysrecovery"></a>wbadmin start sysrecovery



使用指定的参数执行系统恢复（裸机恢复）。

> [!NOTE]
> 此子命令只能从 Windows 恢复环境运行，并且默认情况下不会在**Wbadmin**的使用文本中列出。 有关详细信息，请参阅[Windows 恢复环境（WINDOWS RE）概述](https://technet.microsoft.com/library/hh825173.aspx)。

若要使用此子命令执行系统恢复，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。

## <a name="syntax"></a>语法

```
wbadmin start sysrecovery
-version:<VersionIdentifier>
-backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>}
[-machine:<BackupMachineName>]
[-restoreAllVolumes]
[-recreateDisks]
[-excludeDisks]
[-skipBadClusterCheck]
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-version|以 MM/DD/YYYY： MM 格式指定要恢复的备份的版本标识符。 如果你不知道版本标识符，请键入**wbadmin get 版本**。|
|-backupTarget|指定包含要恢复的备份的存储位置。 当存储位置不同于通常存储此计算机的备份的位置时，此参数非常有用。|
|-计算机|指定要恢复的计算机的名称。 当多台计算机备份到同一位置时，此参数非常有用。 当指定 **-backupTarget**参数时，应使用。|
|-restoreAllVolumes|恢复所选备份中的所有卷。 如果未指定此参数，则仅恢复关键卷（包含系统状态和操作系统组件的卷）。 当你需要在系统恢复过程中恢复非关键卷时，此参数非常有用。|
|-recreateDisks|将磁盘配置恢复到创建备份时存在的状态。</br>警告：此参数删除托管操作系统组件的卷上的所有数据。 它还可能会删除数据卷中的数据。|
|-excludeDisks|仅当使用 **-recreateDisks**参数指定，并且必须以逗号分隔的磁盘标识符列表的形式输入（如**wbadmin get**disk 的输出中所列）时，此参数才有效。 排除的磁盘未分区或未格式化。 此参数有助于保留在恢复操作过程中不需要修改的磁盘上的数据。|
|-skipBadClusterCheck|跳过检查恢复磁盘是否有损坏的群集信息。 如果要还原到备用服务器或硬件，则建议不要使用此参数。 你可以随时在恢复磁盘上手动运行**chkdsk/b**来检查是否有坏群集，然后相应地更新文件系统信息。</br>警告：在运行**Chkdsk**之前，在恢复的系统上报告的坏簇可能不准确。|
|-quiet|运行命令时不提示用户。|

## <a name="examples"></a>示例

若要开始从备份中恢复在 9:00 2013 年3月31日（位于驱动器 d：）上运行的信息，请键入：
```
wbadmin start sysrecovery -version:03/31/2013-09:00 -backupTarget:d:
```
若要开始从备份中恢复运行的信息，请参阅 9:00 2013 年4月30日，位于共享文件夹 \\ \\ servername\shared：对于 server01，请键入：
```
wbadmin start sysrecovery -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBBareMetalRecovery](https://technet.microsoft.com/library/jj902461.aspx) cmdlet