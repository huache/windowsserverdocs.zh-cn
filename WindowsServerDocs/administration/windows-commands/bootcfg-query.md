---
title: bootcfg query
description: 用于从 Boot.ini 查询和显示启动加载器和操作系统部分条目的 bootcfg query 命令的参考文章。
ms.topic: article
ms.assetid: a4cacfd1-10a6-4a11-b0c5-f8abde72bfc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb4ff06e8c0e5f31c0132f7fbc4fad49be53dd62
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880567"
---
# <a name="bootcfg-query"></a>bootcfg query

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

查询并显示来自 Boot.ini 的 [启动加载器] 和 [操作系统] 部分条目。

## <a name="syntax"></a>语法

```
bootcfg /query [/s <computer> [/u <domain>\<user> /p <password>]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="sample-output"></a>示例输出

**Bootcfg/query**命令的示例输出：

```
Boot Loader Settings
----------
timeout: 30
default: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
Boot Entries
------
Boot entry ID:   1
Friendly Name:
path: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
OS Load Options: /fastdetect /debug /debugport=com1:
```

- "**启动加载程序设置**" 区域显示 Boot.ini 的 [启动加载器] 部分中的每个条目。

- "**启动条目**" 区域显示了 Boot.ini 的 [操作系统] 部分中每个操作系统项的更多详细信息。

## <a name="examples"></a>示例

使用**bootcfg/query**命令：

```
bootcfg /query
bootcfg /query /s srvmain /u maindom\hiropln /p p@ssW23
bootcfg /query /u hiropln /p p@ssW23
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
