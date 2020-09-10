---
title: wbadmin get status
description: Wbadmin get status 的参考文章，它报告当前正在运行的备份或恢复操作的状态。
ms.topic: reference
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7dcb1b59de6827500311cfd55245ac6c94a171b0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624597"
---
# <a name="wbadmin-get-status"></a>wbadmin get status



报告当前正在运行的备份或恢复操作的状态。

若要使用此子命令，您必须是 **Backup Operators** 组或 **Administrators** 组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行 **wbadmin** 。  (打开提升的命令提示符，右键单击 " **命令提示符**"，然后单击 "以 **管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

```
wbadmin get status
```

### <a name="parameters"></a>参数

此子命令没有参数。

## <a name="remarks"></a>备注

-   在当前的备份或恢复操作完成之前，此子命令不会停止，即使关闭命令窗口，子命令也会继续运行。
-   如果要停止当前的备份或恢复操作，请使用 **wbadmin stop job** 子命令。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBJob](/powershell/module/windowserverbackup/?view=winserver2012r2-ps) cmdlet
