---
title: wbadmin stop job
description: 用于 wbadmin 停止作业的参考文章，用于取消当前正在运行的备份或恢复操作。 无法重启已取消的操作，必须从头开始重新运行已取消的备份或恢复操作。
ms.topic: reference
ms.assetid: 3b83b398-39c7-4410-bf17-5c1fb1a4f46d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a0ca6fca8dda7c741a9ad9c52a7b6ec0f5e75dea
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031825"
---
# <a name="wbadmin-stop-job"></a>wbadmin stop job



取消当前正在运行的备份或恢复操作。 无法重启已取消的操作，必须从头开始重新运行已取消的备份或恢复操作。

若要使用此子命令停止备份或恢复操作，您必须是 **Backup Operators** 组或 **Administrators** 组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行 **wbadmin** 。  (打开提升的命令提示符，右键单击 " **命令提示符** "，然后单击 "以 **管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

```
wbadmin stop job
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-quiet|对用户运行无提示的子命令。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)