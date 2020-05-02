---
title: 帮助
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d3a16c2534934a7bc8126b0a775ec7aa08462b3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724917"
---
# <a name="help"></a>帮助



提供有关系统命令（即非网络命令）的联机信息。 如果在没有参数的情况下使用，则 "**帮助**" 列出并简要说明每个系统命令。



## <a name="syntax"></a>语法

```
help [<Command>] 
[<Command>] /?
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<命令>|指定您想要了解的命令的名称。|

## <a name="examples"></a>示例

若要查看有关**robocopy**命令的信息，请键入以下命令之一：
```
help robocopy
robocopy /? 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)