---
title: wbadmin disable backup
description: 用于 wbadmin 禁用备份的参考文章，用于停止运行现有的计划每日备份。
ms.topic: article
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98f9e17ff4b1f2ed84af3e703291d02e87841707
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881217"
---
# <a name="wbadmin-disable-backup"></a>wbadmin disable backup



停止运行现有的计划每日备份。

若要禁用计划的每日备份，你必须是**Administrators**组的成员，或者你必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。  (打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

```
wbadmin disable backup
[-quiet]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|-quiet|对用户运行无提示的子命令。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)