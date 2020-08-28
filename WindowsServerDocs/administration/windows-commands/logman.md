---
title: logman
description: Logman 命令的参考文章，用于创建和管理事件跟踪会话和性能日志，并通过命令行支持性能监视器的许多功能。
ms.topic: reference
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b155e3cca0b9f5e35c1c817cfee4e96ca79b6610
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030545"
---
# <a name="logman"></a>logman

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建和管理事件跟踪会话和性能日志，并从命令行支持性能监视器的许多功能。

## <a name="syntax"></a>语法

```
logman [create | query | start | stop | delete| update | import | export | /?] [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [logman create](logman-create.md) | 创建计数器、跟踪、配置数据收集器或 API。 |
| [logman query](logman-query.md) | 查询数据收集器属性。 |
| [logman start &#124; stop](logman-start-stop.md) | 开始或停止数据收集。 |
| [logman delete](logman-delete.md) | 删除现有的数据收集器。 |
| [logman update](logman-update.md) | 更新现有数据收集器的属性。 |
| [logman import &#124; export](logman-import-export.md) | 从 XML 文件导入数据收集器集，或将数据收集器集导出到 XML 文件。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)