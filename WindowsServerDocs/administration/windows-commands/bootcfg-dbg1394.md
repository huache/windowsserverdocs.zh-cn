---
title: bootcfg dbg1394
description: Bootcfg dbg1394 命令的参考主题，它为指定的操作系统条目配置1394端口调试
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 16230c52657fd5c9c14972726ed2465401995223
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709707"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为指定的操作系统项配置1394端口调试。

## <a name="syntax"></a>语法

```
bootcfg /dbg1394 {on | off}[/s <computer> [/u <domain>\<user> /p <password>]] [/ch <channel>] /id <osentrylinenum>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `{on | off}` | 指定1394端口调试的值，包括：<ul><li>**基于.** 通过向指定`<osentrylinenum>`的添加/dbg1394 选项来启用远程调试支持。</li><li>**非.** 通过从指定<osentrylinenum>的中删除/dbg1394 选项来禁用远程调试支持。</li></ul> |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认值为本地计算机。 |
| `/u <domain>\<user>`  | 使用`<user>`或`<domain>\<user>`指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/ch <channel>` | 指定用于调试的通道。 有效值包括1到64之间的整数。 如果禁用了1394端口调试，请勿使用此参数。 |
| `/id <osentrylinenum>` | 指定 Boot.ini 文件的 [操作系统] 部分中添加了操作系统加载选项的操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/dbg1394**命令：

```
bootcfg /dbg1394 /id 2
bootcfg /dbg1394 on /ch 1 /id 3
bootcfg /dbg1394 edit /ch 8 /id 2
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
