---
title: logman create
description: 用于创建计数器、跟踪、配置数据收集器或 API 的 logman create 命令的参考文章。
ms.topic: reference
ms.assetid: 972f0126-7bc4-4b14-9265-062864f3ffd4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1115591f097c81b9b23dedbf3739c10346d4932e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640376"
---
# <a name="logman-create"></a>logman create

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建计数器、跟踪、配置数据收集器或 API。

## <a name="syntax"></a>语法

```
logman create <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [logman create counter](logman-create-counter.md) | 创建计数器数据收集器。 |
| [logman create trace](logman-create-trace.md) | 创建跟踪数据收集器。 |
| [logman create alert](logman-create-alert.md) | 创建警报数据收集器。 |
| [logman create cfg](logman-create-cfg.md) | 创建配置数据收集器。 |
| [logman create api](logman-create-api.md) | 创建 API 跟踪数据收集器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)