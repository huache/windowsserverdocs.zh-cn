---
title: logman 创建 cfg
description: Logman create cfg 命令的参考主题，它用于创建配置数据收集器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bfc87093-3ff5-4e19-aa93-d185fb8e2239
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 518b0c7bddf1d74522a376aafb7da85abb849ac4
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222978"
---
# <a name="logman-create-cfg"></a>logman 创建 cfg

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建配置数据收集器。

## <a name="syntax"></a>语法

```
logman create cfg <[-n] <name>> [options]
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

若要使用注册表项创建名为 cfg_log 的配置数据收集器，请 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\` 键入：

```
logman create cfg cfg_log -reg HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\\
```

若要创建名为 cfg_log 的配置数据收集器（它记录数据库列中的所有 WMI 对象 `root\wmi` `MSNdis_Vendordriverversion` ），请键入：

```
logman create cfg cfg_log -mgt root\wmi:select * FROM MSNdis_Vendordriverversion
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman update cfg 命令](logman-update-cfg.md)

- [logman 命令](logman.md)
