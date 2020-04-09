---
title: wbadmin restore catalog
description: 用于 wbadmin restore catalog 的 Windows 命令主题，该主题从指定的存储位置恢复本地计算机的备份目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce1e24a0-821d-4353-b09d-8f82c5c4ad56
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ce9182e4e405b1538277db25f06b6a49d7240f9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829700"
---
# <a name="wbadmin-restore-catalog"></a>wbadmin restore catalog



从指定的存储位置恢复本地计算机的备份目录。

若要使用此子命令恢复备份目录，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

有关如何使用此子命令的示例，请参阅[示例](#BKMK_examples)。

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
|-计算机|指定要恢复其备份目录的计算机的名称。 当多台计算机的备份存储在同一位置时使用。 当指定 **-backupTarget**时，应使用。|
|-quiet|对用户运行无提示的子命令。|

## <a name="remarks"></a>备注

如果存储备份的位置（磁盘、DVD 或远程共享文件夹）已损坏或丢失，并且无法用于还原备份目录，请使用**wbadmin delete catalog**删除损坏的目录。 在这种情况下，你应在删除备份目录后创建新备份。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要从磁盘 d：上存储的备份还原目录，请键入：
```
wbadmin restore catalog -backupTarget:d
```
若要从共享文件夹中存储的备份还原目录 \\\\servername\share of server01 "，请键入：
```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBCatalog](https://technet.microsoft.com/library/jj902437.aspx) cmdlet