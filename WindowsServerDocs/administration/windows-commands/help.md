---
title: help
description: "\"帮助\" 命令的参考文章，其中显示了可用命令的列表或有关指定命令的详细帮助信息。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 562bb725998cb58eb9a4a9ce9078a833bc0e7781
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924570"
---
# <a name="help"></a>help

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定命令的可用命令或详细帮助信息的列表。 如果在没有参数的情况下使用，则 "**帮助**" 列出并简要说明每个系统命令。

## <a name="syntax"></a>语法

```
help [<command>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<command>` | 指定要显示其详细帮助信息的命令。 |

### <a name="examples"></a>示例

若要查看有关**robocopy**命令的信息，请键入：

```
help robocopy
```

若要显示 DiskPart 中可用的所有命令的列表，请键入：

```
help
```

若要显示有关如何使用 DiskPart 中的**create partition primary**命令的详细帮助信息，请键入：

```
help create partition primary
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
