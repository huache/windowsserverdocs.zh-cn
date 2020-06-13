---
title: nslookup set recurse
description: Nslookup set 递归命令的参考主题，它会告知域名系统（DNS）名称服务器在指定的服务器上找不到该信息时查询其他服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 082ba3bd926d1f47be5510c2340804b1b92991f1
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721598"
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
