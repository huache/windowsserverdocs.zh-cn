---
title: nslookup set recurse
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4386bd5738806016b9ec15802faebf3efdcedf0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723594"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse



告诉域名系统（DNS）名称服务器查询其他服务器（如果没有此信息）。

## <a name="syntax"></a>语法

```
set [no]recurse
```

### <a name="parameters"></a>参数

|   参数   |                                                                  描述                                                                  |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **norecurse** |                停止域名系统（DNS）名称服务器查询其他服务器（如果没有）。                |
|  **recurse**  | 告诉域名系统（DNS）名称服务器查询其他服务器（如果没有此信息）。 默认语法是**递归**的。 |
|     {帮助     |                                                                      ?}                                                                       |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)