---
title: bootcfg ems
description: 适用于 bootcfg ems 的 Windows 命令主题，使用户能够添加或更改用于将紧急管理服务控制台重定向到远程计算机的设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57abdc50-c64a-45f1-8470-3f8c3a51f743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 825426b3ce865f96892f8a8d9b11f11650e1b6c1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848530"
---
# <a name="bootcfg-ems"></a>bootcfg ems

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

允许用户添加或更改用于将紧急管理服务控制台重定向到远程计算机的设置。 通过启用紧急管理服务，你可以向 Boot.ini 文件的 [boot loader] 部分添加一个重定向 = 端口号行，并向指定的操作系统条目行添加一个/redirect 选项。 仅在服务器上启用 "紧急管理服务" 功能。

## <a name="syntax"></a>语法
```
bootcfg /ems {ON | OFF | edit} [/s <computer> [/u <Domain>\<User> /p <Password>]] [/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <OSEntryLineNum>]
```
### <a name="parameters"></a>参数

|                            参数                             |                                                                                                                                                                                                                                                                                                                                                              说明                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                    {ON &#124; OFF&#124;编辑}                    | 指定紧急管理服务重定向的值。<p>**启用-启用**指定 <OSEntryLineNum>的远程输出。 将/redirect 选项添加到指定的 <OSEntryLineNum>，将重定向 = com<X> 设置添加到 [启动加载器] 部分。 Com<X> 的值由 **/port**参数设置。<p>**OFF** -禁用到远程计算机的输出。 从 [启动加载程序] 部分删除指定 <OSEntryLineNum> 和重定向 = com<X> 设置中的/redirect 选项。<p>**编辑**-允许通过在 [启动加载程序] 部分中更改重定向 = com<X> 设置来更改端口设置。 Com<X> 的值重置为 **/port**参数指定的值。 |
|                          /s <computer>                           |                                                                                                                                                                                                                                                                                                          指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                                                                                                                                                                                                                                                                                           |
|                       /u <Domain>\\<User>                        |                                                                                                                                                                                                                                                                 使用 <User> 或 <Domain>\\<User>指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。                                                                                                                                                                                                                                                                  |
|                          /p <Password>                           |                                                                                                                                                                                                                                                                                                                         指定在 **/u**参数中指定的用户帐户的密码。                                                                                                                                                                                                                                                                                                                         |
| /port {COM1 &#124; COM2 &#124; COM3 &#124; COM4 &#124; BIOSSET}  |                                                                                                                                                                                                                              指定用于重定向的 COM 端口。 **BIOSSET**指导紧急管理服务获取 BIOS 设置，以确定应使用哪个端口进行重定向。 如果正在禁用远程管理的输出，请不要使用 **/port**参数。                                                                                                                                                                                                                              |
| /baud {9600 &#124; 19200 &#124; 38400&#124; 57600 &#124; 115200} |                                                                                                                                                                                                                                                                                               指定用于重定向的波特率。 如果正在禁用远程管理的输出，请不要使用 **/baud**参数。                                                                                                                                                                                                                                                                                               |
|                       /id <OSEntryLineNum>                       |                                                                                                                                                                                              指定操作系统输入行号，"紧急管理服务" 选项将添加到 Boot.ini 文件的 [操作系统] 部分。 [操作系统] 部分标题后面的第一行是1。 当 "紧急管理服务" 值设置为 **"开" 或 "** **关**" 时，此参数是必需的。                                                                                                                                                                                              |
|                                /?                                |                                                                                                                                                                                                                                                                                                                                                 在命令提示符下显示帮助。                                                                                                                                                                                                                                                                                                                                                  |

## <a name="examples"></a><a name=BKMK_examples></a>示例
下面的示例演示如何使用**bootcfg/ems**命令：
```
bootcfg /ems on /port com1 /baud 19200 /id 2 
bootcfg /ems on /port biosset /id 3 
bootcfg /s srvmain /ems off /id 2 
bootcfg /ems edit /port com2 /baud 115200 
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /ems off /id 2
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
