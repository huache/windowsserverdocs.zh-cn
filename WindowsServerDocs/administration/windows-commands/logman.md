---
title: logman
description: Logman 命令的参考主题，可用于创建和管理事件跟踪会话和性能日志，并通过命令行支持性能监视器的许多功能。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44b5e134440d71eed61ca8e03739abcc962df1f9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820547"
---
# <a name="logman"></a>logman

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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