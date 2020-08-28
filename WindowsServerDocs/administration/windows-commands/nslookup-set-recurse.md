---
title: nslookup set recurse
description: "\"Nslookup 集递归\" 命令的参考文章，它告知域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。"
ms.topic: reference
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 57c881dc101df2ebf8d659f29340a9fcb574cce6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025201"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse

告诉域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。

## <a name="syntax"></a>语法

```
set [no]recurse
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| norecurse | 如果 DNS) 名称服务器在指定的服务器上找不到该信息，则停止域名系统 (DNS 名称服务器查询其他服务器。 |
| recurse | 告诉域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
