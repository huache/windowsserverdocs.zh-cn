---
title: wbadmin 停止作业
description: Wbadmin 停止作业的参考主题，用于取消当前正在运行的备份或恢复操作。 无法重启已取消的操作，必须从头开始重新运行已取消的备份或恢复操作。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3b83b398-39c7-4410-bf17-5c1fb1a4f46d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3133688ac0d60d97d80192611c9b561c53a74c35
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725840"
---
# <a name="wbadmin-stop-job"></a>wbadmin 停止作业



取消当前正在运行的备份或恢复操作。 无法重启已取消的操作，必须从头开始重新运行已取消的备份或恢复操作。

若要使用此子命令停止备份或恢复操作，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin stop job
[-quiet]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|-quiet|对用户运行无提示的子命令。|

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)