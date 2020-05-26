---
title: 帮助
description: Help 命令的参考主题，该主题显示有关指定命令的可用命令或详细帮助信息的列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b73ef32b49b834a91f24e943749eb21398c8588
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818657"
---
# <a name="help"></a>帮助

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
