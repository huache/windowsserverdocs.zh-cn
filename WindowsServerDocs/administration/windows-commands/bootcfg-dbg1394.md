---
title: bootcfg dbg1394
description: 适用于 bootcfg dbg1394 的 Windows 命令主题，它为指定的操作系统条目配置1394端口调试
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d49e0a39cd021f093ca68bf97963dc35c3b53ad4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848670"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

为指定的操作系统项配置1394端口调试。

## <a name="syntax"></a>语法
```
bootcfg /dbg1394 {ON | OFF}[/s <computer> [/u <Domain>\<User> /p <Password>]] [/ch <Channel>] /id <OSEntryLineNum>
```
### <a name="parameters"></a>参数

|      参数       |                                                                                                                                           说明                                                                                                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   {ON &#124; OFF}    | 指定1394端口调试的值。<p>-   启用-通过将/dbg1394 选项添加到**指定的 <OSEntryLineNum>** 来启用远程调试支持。<br />-   **OFF** -通过删除指定 <OSEntryLineNum>中的/dbg1394 选项来禁用远程调试支持。 |
|    /s <computer>     |                                                                                        指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                                                                        |
| /u <Domain>\\<User>  |                                               使用 <User> 或 <Domain>\\<User>指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。                                               |
|    /p <Password>     |                                                                                                      指定在 **/u**参数中指定的用户帐户的密码。                                                                                                       |
|     /ch 通道      |                                                           指定用于调试的通道。 有效值为1到64之间的整数。 如果正在禁用1394端口调试，请不要使用 **/ch** <Channel> 参数。                                                           |
| /id <OSEntryLineNum> |                                  指定 Boot.ini 文件的 [操作系统] 部分中添加了1394端口调试选项的操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。                                  |
|          /?          |                                                                                                                               在命令提示符下显示帮助。                                                                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>示例
下面的示例演示如何使用**bootcfg/dbg1394**命令：
```
bootcfg /dbg1394 /id 2 
bootcfg /dbg1394 on /ch 1 /id 3 
bootcfg /dbg1394 edit /ch 8 /id 2 
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
