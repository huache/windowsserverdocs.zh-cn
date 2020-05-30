---
title: logman update
description: 用于更新现有数据收集器的 logman update 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c98af84f-64ba-40c3-826d-75b80dfb9b34
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0302607f3d2efd9c20f8629e73199567a459d7c8
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222746"
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
| [logman 更新计数器](logman-update-counter.md) | 更新计数器数据收集器。 |
| [logman 更新警报](logman-update-alert.md) | 更新警报数据收集器。 |
| [logman 更新 cfg](logman-update-cfg.md) | 更新配置数据收集器。 |
| [logman 更新 api](logman-update-api.md) | 更新 API 跟踪数据收集器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
