---
title: logman 启动和 logman 停止
description: 用于启动数据收集器并将开始时间设置为手动的 logman start 和 logman 停止命令的参考主题，或停止数据收集器集并将结束时间设置为手动。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: db0111c4f58f0a28ad76affd3e4d8e24d4a927c2
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222917"
---
# <a name="logman-start-and-logman-stop"></a>logman 启动和 logman 停止

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

**Logman start**命令启动一个数据收集器，并将开始时间设置为 "手动"。 **Logman stop**命令停止数据收集器集，并将结束时间设置为 "手动"。

## <a name="syntax"></a>语法

```
logman start <[-n] <name>> [options]
logman stop <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| [-n]`<name>` | 指定目标对象的名称。 |
| -ets | 直接将命令发送到事件跟踪会话，而不保存或计划。 |
| -as | 异步执行请求的操作。 |
| -? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要启动数据收集器*perf_log*，请在 "远程计算机" *server_1*上键入：

```
logman start perf_log -s server_1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
