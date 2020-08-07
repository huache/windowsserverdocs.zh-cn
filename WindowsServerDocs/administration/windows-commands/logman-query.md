---
title: logman query
description: 用于查询数据收集器或数据收集器集属性的 logman 查询命令的参考文章。
ms.topic: article
ms.assetid: 1116a0f0-5415-4369-a045-12f79f8f66de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2cb324651001f071e45acf0821f402458ed838d8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887288"
---
# <a name="logman-query"></a>logman query

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

查询数据收集器或数据收集器集属性。

## <a name="syntax"></a>语法

```
logman query [providers|Data Collector Set name] [options]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| [-n]`<name>` | 目标对象的名称。 |
| -ets | 直接向事件跟踪会话发送命令，而无需保存或计划。 |
| /? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要列出在目标系统上配置的所有数据收集器集，请键入：

```
logman query
```

若要列出名为*perf_log*的数据收集器集中包含的数据收集器，请键入：

```
logman query perf_log
```

若要列出目标系统上所有可用的数据收集器，请键入：

```
logman query providers
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
