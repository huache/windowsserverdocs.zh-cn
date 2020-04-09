---
title: bootcfg query
description: 用于 bootcfg 查询的 Windows 命令主题，它查询并显示 boot.ini 中的启动加载器和操作系统部分条目。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a4cacfd1-10a6-4a11-b0c5-f8abde72bfc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ac80c802b1d30dcf7221f94f761233c6b6fc6b6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848520"
---
# <a name="bootcfg-query"></a>bootcfg query

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

查询并显示 Boot.ini 中的 [启动加载程序] 和 [操作系统] 部分条目。

## <a name="syntax"></a>语法
```
bootcfg /query [/s <computer> [/u <Domain>\<User> /p <Password>]]
```
### <a name="parameters"></a>参数

|        术语         |                                                                                             Definition                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>    |                                         指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                          |
| /u <Domain>\\<User> | 使用 <User>或 <Domain>\\<User>指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
|    /p <Password>    |                                                        指定在 **/u**参数中指定的用户帐户的密码。                                                        |
|         /?          |                                                                                在命令提示符下显示帮助。                                                                                 |

##### <a name="remarks"></a>备注
- 下面是一个**bootcfg/query**输出示例：
  ```
  Boot Loader Settings
  ----------
  timeout: 30
  default: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  Boot Entries
  ------
  Boot entry ID:   1
  Friendly Name:   
  path:            multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  OS Load Options: /fastdetect /debug /debugport=com1:
  ```
- **Bootcfg 查询**输出的启动加载器设置部分显示 boot.ini 的 [boot loader] 部分中的每个条目。
- **Bootcfg 查询**输出的启动条目部分显示 boot.ini 的 [操作系统] 部分中每个操作系统项的以下详细信息：启动项 ID、友好名称、路径和 OS 加载选项。
  ## <a name="examples"></a><a name=BKMK_examples></a>示例
  下面的示例演示如何使用**bootcfg/query**命令：
  ```
  bootcfg /query
  bootcfg /query /s srvmain /u maindom\hiropln /p p@ssW23
  bootcfg /query /u hiropln /p p@ssW23
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法项](command-line-syntax-key.md)
