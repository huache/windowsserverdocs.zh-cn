---
title: logman create
description: Logman create 命令的参考主题，用于创建计数器、跟踪、配置数据收集器或 API。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 972f0126-7bc4-4b14-9265-062864f3ffd4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4a68be098f868cdd9cd48c1e7c68fc183fa1fab
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222956"
---
# <a name="logman-create"></a>logman create

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建计数器、跟踪、配置数据收集器或 API。

## <a name="syntax"></a>语法

```
logman create <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [logman create 计数器](logman-create-counter.md) | 创建计数器数据收集器。 |
| [logman 创建跟踪](logman-create-trace.md) | 创建跟踪数据收集器。 |
| [logman 创建警报](logman-create-alert.md) | 创建警报数据收集器。 |
| [logman 创建 cfg](logman-create-cfg.md) | 创建配置数据收集器。 |
| [logman 创建 api](logman-create-api.md) | 创建 API 跟踪数据收集器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)