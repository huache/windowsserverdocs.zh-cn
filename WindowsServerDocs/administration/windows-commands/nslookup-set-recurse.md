---
title: nslookup set recurse
description: "\"Nslookup 集递归\" 命令的参考文章，它告知域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。"
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 26a98e646f0915a684129d4b0205384f10c31d49
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885577"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse

告诉域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。

## <a name="syntax"></a>语法

```
set [no]recurse
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---------- | ---------- |
| norecurse | 如果 DNS) 名称服务器在指定的服务器上找不到该信息，则停止域名系统 (DNS 名称服务器查询其他服务器。 |
| recurse | 告诉域名系统 (DNS) 名称服务器在指定的服务器上找不到该信息时查询其他服务器。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
