---
title: logman import and logman export
description: 用于从 XML 文件导入数据收集器集或将数据收集器集导出到 XML 文件的 logman 导入和 logman 导出的参考文章。
ms.topic: article
ms.assetid: c258daba-fb93-47c0-a53b-2fe83ed2c743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d09d0e517acf19ba1cbb167eb24b16aea3ff2bc
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887295"
---
# <a name="logman-import-and-logman-export"></a>logman import and logman export

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从 XML 文件导入数据收集器集，或将数据收集器集导出到 XML 文件。

## <a name="syntax"></a>语法

```
logman import <[-n] <name> <-xml <name> [options]
logman export <[-n] <name> <-xml <name> [options]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| [-n]`<name>` | 目标对象的名称。 |
| -xml`<name>` | 要导入或导出的 XML 文件的名称。 |
| -ets | 直接向事件跟踪会话发送命令，而无需保存或计划。 |
| -[-] u`<user [password]>` | 指定要以其身份运行的用户。 输入 `*` 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| -y | 在不提示的情况下回答 "是"。 |
| /? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要从计算机导*c:\windows\perf_log.xml*入 XML 文件c:\windows\perf_log.xml*server_1*作为名为*perf_log*的数据收集器集，请键入：

```
logman import perf_log -s server_1 -xml c:\windows\perf_log.xml
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
