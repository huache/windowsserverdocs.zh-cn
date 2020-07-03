---
title: nslookup set recurse
description: 用于 nslookup set 递归命令的参考文章，此命令告知域名系统（DNS）名称服务器在无法在指定的服务器上找到信息时查询其他服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dd65eaa9ba60e2a3cdf79e808b2efccb28b7d455
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935691"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse

如果域名系统（DNS）名称服务器找不到指定服务器上的信息，则通知该服务器查询其他服务器。

## <a name="syntax"></a>语法

```
set [no]recurse
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| norecurse | 如果域名系统（DNS）名称服务器找不到指定服务器上的信息，则阻止该服务器查询其他服务器。 |
| recurse | 如果域名系统（DNS）名称服务器找不到指定服务器上的信息，则通知该服务器查询其他服务器。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
