---
title: logman 更新 cfg
description: Logman update cfg 命令的参考主题，用于更新现有配置数据收集器的属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9da4e8b4-3be5-42d3-b0b4-c429630c35c4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af4d61372aa5b10d5bb2a5c93e16df391eadfd2f
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222786"
---
# <a name="logman-update-cfg"></a>logman 更新 cfg

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更新现有配置数据收集器的属性。

## <a name="syntax"></a>语法

```
logman update cfg <[-n] <name>> [options]
```

### <a name="parameters"></a>参数


| 参数 | 说明 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| [-n]`<name>` | 目标对象的名称。 |
| -[-] u`<user [password]>` | 指定要以其身份运行的用户。 输入 \* 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| -m`<[start] [stop] [[start] [stop] [...]]>` | 更改为手动启动或停止，而不是计划的开始或结束时间。 |
| -rf`<[[hh:]mm:]ss>` | 在指定的时间段内运行数据收集器。 |
| -b`<M/d/yyyy h:mm:ss[AM|PM]>` | 开始在指定时间收集数据。 |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | 结束在指定时间收集的数据。 |
| -si`<[[hh:]mm:]ss>` | 指定性能计数器数据收集器的采样间隔。 |
| -o`<path|dsn!log>` | 指定 SQL 数据库中的输出日志文件或 DSN 和日志集名称。 |
| -[-] r | 每日在指定的开始和结束时间重复数据收集器。 |
| -[-] a | 追加现有的日志文件。 |
| -[-] o | 覆盖现有的日志文件。 |
| -[-] v`<nnnnnn|mmddhhmm>` | 将文件版本信息附加到日志文件名称的末尾。 |
| -[-] rc`<task>` | 运行每次关闭日志时指定的命令。 |
| -[-] 最大值`<value>` | 最大日志文件大小（MB）或 SQL 日志的最大记录数。 |
| -[-] .cnf`<[[hh:]mm:]ss>` | 指定 time 后，在指定的时间过后，将创建一个新的文件。 如果未指定时间，则在超出最大大小时创建新文件。 |
| -y | 在不提示的情况下回答 "是"。 |
| -[-] ni | 启用（-ni）或禁用（-ni）网络接口查询。 |
| -reg`<path [path [...]]>` | 指定要收集的注册表值。 |
| -进行中`<query [query [...]]>` | 指定要使用 SQL 查询语言收集的 WMI 对象。 |
| -ftc`<path [path [...]]>` | 指定要收集的文件的完整路径。 |
| /? | 显示区分上下文的帮助。 |

#### <a name="remarks"></a>备注

- 其中列出了 [-]，添加额外的连字符（-）将对选项求反。

### <a name="examples"></a>示例

若要更新名为*cfg_log*的配置数据收集器来收集注册表项 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\` ，请键入：

```
logman update cfg cfg_log -reg HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman create cfg 命令](logman-create-cfg.md)

- [logman 命令](logman.md)
