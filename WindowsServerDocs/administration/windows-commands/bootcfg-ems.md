---
title: bootcfg ems
description: Bootcfg ems 命令的参考主题，使用户能够添加或更改将紧急管理服务控制台重定向到远程计算机的设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57abdc50-c64a-45f1-8470-3f8c3a51f743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c85231e094852feb673eb4f99b183f06014234b2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709521"
---
# <a name="bootcfg-ems"></a>bootcfg ems

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

允许用户添加或更改用于将紧急管理服务控制台重定向到远程计算机的设置。 启用紧急管理服务后，会`redirect=Port#`将一个行添加到 boot.ini 文件的 [boot loader] 部分，并将/redirect 选项添加到指定的操作系统条目行。 仅在服务器上启用 "紧急管理服务" 功能。

## <a name="syntax"></a>语法

```
bootcfg /ems {on | off | edit}[/s <computer> [/u <domain>\<user> /p <password>]] [/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `{on | off | edit}` | 指定紧急管理服务重定向的值，包括：<ul><li>**基于.** 启用指定`<osentrylinenum>`的远程输出。 还会将/redirect 选项添加到指定<osentrylinenum>的和`redirect=com<X>` [启动加载程序] 部分的设置。 的值`com<X>`由 **/port**参数设置。</li><li>**非.** 禁用到远程计算机的输出。 还将从 [启动加载程序] <osentrylinenum>部分中`redirect=com<X>`删除指定的/redirect 选项和设置。</li><li>**编辑.** 允许通过更改 [启动加载程序] `redirect=com<X>`部分中的设置来更改端口设置。 的值`com<X>`由 **/port**参数设置。</li></ul> |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认值为本地计算机。 |
| `/u <domain>\<user>`  | 使用`<user>`或`<domain>\<user>`指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}` |  指定用于重定向的 COM 端口。 BIOSSET 参数指示紧急管理服务获取 BIOS 设置，以确定应使用哪个端口进行重定向。 如果禁用了远程管理的输出，请不要使用此参数。 |
| `/baud {9600 | 19200 | 38400 | 57600 | 115200}` | 指定用于重定向的波特率。 如果禁用了远程管理的输出，请不要使用此参数。 |
| `/id <osentrylinenum>` | 指定操作系统输入行号，"紧急管理服务" 选项将添加到 Boot.ini 文件的 [操作系统] 部分。 [操作系统] 部分标题后面的第一行是1。 当 "紧急管理服务" 值设置为 **"开" 或 "** **关**" 时，此参数是必需的。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/ems**命令：

```
bootcfg /ems on /port com1 /baud 19200 /id 2
bootcfg /ems on /port biosset /id 3
bootcfg /s srvmain /ems off /id 2
bootcfg /ems edit /port com2 /baud 115200
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /ems off /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
