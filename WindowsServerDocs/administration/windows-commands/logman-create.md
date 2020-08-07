---
title: logman create
description: 用于创建计数器、跟踪、配置数据收集器或 API 的 logman create 命令的参考文章。
ms.topic: article
ms.assetid: 972f0126-7bc4-4b14-9265-062864f3ffd4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd236b7ad78921c9f32094b5e595b4125fe2ec74
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887346"
---
# <a name="logman-create"></a>logman create

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建计数器、跟踪、配置数据收集器或 API。

## <a name="syntax"></a>语法

```
logman create <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [logman create counter](logman-create-counter.md) | 创建计数器数据收集器。 |
| [logman create trace](logman-create-trace.md) | 创建跟踪数据收集器。 |
| [logman create alert](logman-create-alert.md) | 创建警报数据收集器。 |
| [logman create cfg](logman-create-cfg.md) | 创建配置数据收集器。 |
| [logman create api](logman-create-api.md) | 创建 API 跟踪数据收集器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)