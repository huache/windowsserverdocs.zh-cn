---
title: bootcfg delete
description: Bootcfg delete 命令的参考文章，可用于删除 Boot.ini 文件的操作系统部分中的操作系统条目。
ms.topic: reference
ms.assetid: 71382e29-9b39-41c8-9c23-cf0ff829440a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f848d42e9b6cabb8fe5765d1c5c5cb9b9b982e0c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630214"
---
# <a name="bootcfg-delete"></a>bootcfg delete

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除 Boot.ini 文件的 [操作系统] 部分中的操作系统项。

## <a name="syntax"></a>语法

```
bootcfg /delete [/s <computer> [/u <domain>\<user> /p <password>]] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u** 参数中指定的用户帐户的密码。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用 **bootcfg/delete** 命令：

```
bootcfg /delete /id 1
bootcfg /delete /s srvmain /u maindom\hiropln /p p@ssW23 /id 3
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
