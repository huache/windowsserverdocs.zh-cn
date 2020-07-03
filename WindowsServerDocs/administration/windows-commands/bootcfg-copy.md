---
title: bootcfg copy
description: 用于生成现有启动项的副本的 bootcfg copy 命令的参考文章，可将命令行选项添加到其中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2a236c2a-8675-444d-b695-9cbc9aff643b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b158e4b9f892c0142d03281b6608f911afdf7b0a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925000"
---
# <a name="bootcfg-copy"></a>bootcfg copy

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建现有启动项的副本，您可以将命令行选项添加到该副本中。

## <a name="syntax"></a>语法

```
bootcfg /copy [/s <computer> [/u <domain>\<user> /p <password>]] [/d <description>] [/id <osentrylinenum>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/d <description>` | 指定新操作系统项的说明。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要复制启动条目1并输入 \ABC Server \ 作为说明：

```
bootcfg /copy /d \ABC Server\ /id 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
