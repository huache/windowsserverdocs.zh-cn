---
title: logman 导入和 logman 导出
description: 用于从 XML 文件导入数据收集器集或将数据收集器集导出到 XML 文件的 logman 导入和 logman 导出的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c258daba-fb93-47c0-a53b-2fe83ed2c743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ce18c615d45d4922c8819d30ff47d54328111170
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222940"
---
# <a name="logman-import-and-logman-export"></a>logman 导入和 logman 导出

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从 XML 文件导入数据收集器集，或将数据收集器集导出到 XML 文件。

## <a name="syntax"></a>语法

```
logman import <[-n] <name>> <-xml <name>> [options]
logman export <[-n] <name>> <-xml <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
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

若要从计算机*server_1*将 xml 文件 c:\windows\ 作为名为*perf_log*的数据收集器集导入*perf_log* ，请键入：

```
logman import perf_log -s server_1 -xml c:\windows\perf_log.xml
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
