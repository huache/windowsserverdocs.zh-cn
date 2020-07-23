---
title: wbadmin get disks
description: Wbadmin get 磁盘的参考文章，其中列出了本地计算机当前联机的内部和外部磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 320edef1-df11-446b-a183-9f81811ef938
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b42deb873613a03e985fc9d54f954c4fd6bfb97
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954649"
---
# <a name="wbadmin-get-disks"></a>wbadmin get disks



列出本地计算机当前处于联机状态的内部和外部磁盘。

若要列出使用此子命令联机的磁盘，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin get disks
```

### <a name="parameters"></a>参数

此子命令没有参数。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBDisk](/powershell/module/windowserverbackup/?view=winserver2012r2-ps) cmdlet
