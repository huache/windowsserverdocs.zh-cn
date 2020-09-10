---
title: logman delete
description: 用于删除现有数据收集器的 logman delete 命令的参考文章。
ms.topic: reference
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 57d909a23e65de3c74daff4fe82f42943cb3875d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634369"
---
# <a name="logman-delete"></a>logman delete

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除现有的数据收集器。

## <a name="syntax"></a>语法

```
logman delete <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s `<computer name>` | 在指定的远程计算机上执行命令。 |
| -config `<value>` | 指定包含命令选项的设置文件。 |
| [-n] `<name>` | 目标对象的名称。 |
| -ets | 直接向事件跟踪会话发送命令，而无需保存或计划。 |
| -[-] u `<user [password]>` | 指定要以其身份运行的用户。 输入 \* 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| /? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要删除数据收集器 *perf_log*，请键入：

```
logman delete perf_log
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 命令](logman.md)
