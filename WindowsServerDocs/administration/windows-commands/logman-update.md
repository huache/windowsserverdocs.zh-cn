---
title: logman update
description: 用于更新现有数据收集器的 logman update 命令的参考文章。
ms.topic: reference
ms.assetid: c98af84f-64ba-40c3-826d-75b80dfb9b34
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5d72e9f65a9820b67631e46cad4e8d506016738a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627461"
---
# <a name="logman-update"></a>logman update

更新现有的数据收集器。

## <a name="syntax"></a>语法

```
logman update <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------| ----------- |
| [logman update counter](logman-update-counter.md) | 更新计数器数据收集器。 |
| [logman update alert](logman-update-alert.md) | 更新警报数据收集器。 |
| [logman update cfg](logman-update-cfg.md) | 更新配置数据收集器。 |
| [logman update api](logman-update-api.md) | 更新 API 跟踪数据收集器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
