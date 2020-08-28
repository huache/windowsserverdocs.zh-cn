---
title: bootcfg dbg1394
description: Bootcfg dbg1394 命令的参考文章，该命令为指定的操作系统条目配置1394端口调试
ms.topic: reference
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f24561751d3a41bf1bf12148dc550f0a56c159c6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034525"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为指定的操作系统项配置1394端口调试。

## <a name="syntax"></a>语法

```
bootcfg /dbg1394 {on | off}[/s <computer> [/u <domain>\<user> /p <password>]] [/ch <channel>] /id <osentrylinenum>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `{on | off}` | 指定1394端口调试的值，包括：<ul><li>**基于.** 通过向指定的添加/dbg1394 选项来启用远程调试支持 `<osentrylinenum>` 。</li><li>**非.** 通过从指定的中删除/dbg1394 选项来禁用远程调试支持 <osentrylinenum> 。</li></ul> |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u** 参数中指定的用户帐户的密码。 |
| `/ch <channel>` | 指定用于调试的通道。 有效值包括1到64之间的整数。 如果禁用了1394端口调试，请勿使用此参数。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用 **bootcfg/dbg1394**命令：

```
bootcfg /dbg1394 /id 2
bootcfg /dbg1394 on /ch 1 /id 3
bootcfg /dbg1394 edit /ch 8 /id 2
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
