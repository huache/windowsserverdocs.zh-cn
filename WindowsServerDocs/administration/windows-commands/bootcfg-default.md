---
title: bootcfg default
description: 适用于 bootcfg 默认值的 Windows 命令主题，它指定要指定为默认的操作系统项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e21824d7-8278-41d7-a2c5-ce09803d513a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 517cf444a5517b3d612266b57b428e47ac60d4ef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848561"
---
# <a name="bootcfg-default"></a>bootcfg default

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定要指定为默认的操作系统项。

## <a name="syntax"></a>语法
```
bootcfg /default [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
### <a name="parameters"></a>参数

|      参数       |                                                                                             说明                                                                                              |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                          指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                          |
| /u <Domain>\\<User>  | 使用 <User> 或 <Domain>\\<User>指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
|    /p <Password>     |                                                        指定在 **/u**参数中指定的用户帐户的密码。                                                         |
| /id <OSEntryLineNum> | 指定 Boot.ini 文件的 [操作系统] 部分中的操作系统条目行号，以指定为默认值。 [操作系统] 部分标题后面的第一行是1。  |
|          /?          |                                                                                 在命令提示符下显示帮助。                                                                                 |

## <a name="examples"></a><a name=BKMK_examples></a>示例
下面的示例演示如何使用**bootcfg/默认 27000**命令：
```
bootcfg /default /id 2
bootcfg /default /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
