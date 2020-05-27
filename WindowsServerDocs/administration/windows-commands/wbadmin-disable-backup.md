---
title: wbadmin 禁用备份
description: Wbadmin 禁用备份的参考主题，它停止运行现有的计划每日备份。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6bc211946c908b44b196995a9e5000d6ff3b7f82
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821417"
---
# <a name="wbadmin-disable-backup"></a>wbadmin 禁用备份



停止运行现有的计划每日备份。

若要禁用计划的每日备份，你必须是**Administrators**组的成员，或者你必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin disable backup
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-quiet|对用户运行无提示的子命令。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)