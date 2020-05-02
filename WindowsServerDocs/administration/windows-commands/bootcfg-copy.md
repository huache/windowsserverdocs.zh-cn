---
title: bootcfg copy
description: Bootcfg copy 命令的参考主题，该命令会生成现有启动项的副本，您可以将命令行选项添加到该副本中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2a236c2a-8675-444d-b695-9cbc9aff643b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 033227ab1d9efcdf1d58708a75085067766a6af2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709684"
---
# <a name="bootcfg-copy"></a>bootcfg copy

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建现有启动项的副本，您可以将命令行选项添加到该副本中。

## <a name="syntax"></a>语法

```
bootcfg /copy [/s <computer> [/u <domain>\<user> /p <password>]] [/d <description>] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认值为本地计算机。 |
| `/u <domain>\<user>`  | 使用`<user>`或`<domain>\<user>`指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/d <description>` | 指定新操作系统项的说明。 |
| `/id <osentrylinenum>` | 指定 Boot.ini 文件的 [操作系统] 部分中添加了操作系统加载选项的操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要复制启动条目1并输入 \ABC Server \ 作为说明：

```
bootcfg /copy /d \ABC Server\ /id 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
