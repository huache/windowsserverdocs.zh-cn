---
title: bootcfg delete
description: Bootcfg delete 命令的参考文章，可用于删除 Boot.ini 文件的操作系统部分中的操作系统条目。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 71382e29-9b39-41c8-9c23-cf0ff829440a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2a4176cb0935938b4b174953d05cd09af3db62b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926283"
---
# <a name="bootcfg-delete"></a>bootcfg delete

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除 Boot.ini 文件的 [操作系统] 部分中的操作系统项。

## <a name="syntax"></a>语法

```
bootcfg /delete [/s <computer> [/u <domain>\<user> /p <password>]] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/delete**命令：

```
bootcfg /delete /id 1
bootcfg /delete /s srvmain /u maindom\hiropln /p p@ssW23 /id 3
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
