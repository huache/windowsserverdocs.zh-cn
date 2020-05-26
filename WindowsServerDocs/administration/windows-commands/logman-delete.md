---
title: logman delete
description: 用于删除现有数据收集器的 logman delete 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af13e802a1b11636a3cbfe7c908f6d26497cf506
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820577"
---
# <a name="logman-delete"></a>logman delete

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除现有的数据收集器。

## <a name="syntax"></a>语法

```
logman delete <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| [-n]`<name>` | 目标对象的名称。 |
| -ets | 直接向事件跟踪会话发送命令，而无需保存或计划。 |
| -[-] u`<user [password]>` | 指定要以其身份运行的用户。 输入 \* 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| /? | 显示区分上下文的帮助。 |

### <a name="examples"></a>示例

若要删除数据收集器*perf_log*，请键入：

```
logman delete perf_log
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman](logman.md)
