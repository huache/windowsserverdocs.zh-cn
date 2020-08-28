---
title: logman start and logman stop
description: 用于启动数据收集器并将开始时间设置为手动的 logman start 和 logman 停止命令的参考文章，或停止数据收集器集并将结束时间设置为手动。
ms.topic: reference
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b573ecd78ad9f062162d2c1ad16d59aebe740ee
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038858"
---
# <a name="logman-start-and-logman-stop"></a>logman start and logman stop

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

**Logman start**命令启动一个数据收集器，并将开始时间设置为 "手动"。 **Logman stop**命令停止数据收集器集，并将结束时间设置为 "手动"。

## <a name="syntax"></a>语法

```
logman start <[-n] <name>> [options]
logman stop <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s `<computer name>` | 在指定的远程计算机上执行命令。 |
| -config `<value>` | 指定包含命令选项的设置文件。 |
| [-n] `<name>` | 指定目标对象的名称。 |
| -ets | 直接将命令发送到事件跟踪会话，而不保存或计划。 |
| -as | 异步执行请求的操作。 |
| -? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要启动数据收集器 *perf_log*，请在 "远程计算机" *server_1*上键入：

```
logman start perf_log -s server_1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
