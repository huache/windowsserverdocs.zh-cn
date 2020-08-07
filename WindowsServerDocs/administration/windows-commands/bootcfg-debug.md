---
title: bootcfg debug
description: "\"Bootcfg 调试\" 命令的参考文章，用于为指定的操作系统条目添加或更改调试设置。"
ms.topic: article
ms.assetid: 28afa5fb-a236-46e2-b1a4-a3c43a49c437
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b3cbde64da67196a1067791e5dad3c2b02756d4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880689"
---
# <a name="bootcfg-debug"></a>bootcfg debug

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

添加或更改指定操作系统项的调试设置。

>[!NOTE]
> 如果尝试调试端口1394，请改用[bootcfg dbg1394](bootcfg-dbg1394.md)命令。

## <a name="syntax"></a>语法

```
bootcfg /debug {on | off | edit}[/s <computer> [/u <domain>\<user> /p <password>]] [/port {COM1 | COM2 | COM3 | COM4}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `{on | off | edit}` | 指定端口调试的值，包括：<ul><li>**基于.** 通过将/debug 选项添加到指定的，启用远程调试支持 `<osentrylinenum>` 。</li><li>**非.** 通过从指定的中删除/debug 选项来禁用远程调试支持 <osentrylinenum> 。</li><li>**编辑.** 通过更改与指定的/debug 选项关联的值，允许更改端口和波特率设置 <osentrylinenum> 。</li></ul> |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/port {COM1 | COM2 | COM3 | COM4}` |  指定用于调试的 COM 端口。 如果禁用调试，请勿使用此参数。 |
| `/baud {9600 | 19200 | 38400 | 57600 | 115200}` | 指定用于调试的波特率。 如果禁用调试，请勿使用此参数。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/debug**命令：

```
bootcfg /debug on /port com1 /id 2
bootcfg /debug edit /port com2 /baud 19200 /id 2
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /debug off /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
