---
title: fsutil wim
description: Fsutil wim 命令的参考主题，它提供了用于发现和管理 Windows 映像（WIM）的文件的功能。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: db6a946eac59269d2bb4072c46552ac84366ed40
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436822"
---
# <a name="fsutil-wim"></a>fsutil wim

> 适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows 10

提供用于发现和管理支持 Windows 映像（WIM）的文件的函数。

## <a name="syntax"></a>语法

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| enumfiles | 枚举支持 WIM 的文件。 |
| `<drive name>` | 指定驱动器名称。 |
| `<data source>` | 指定数据源。 |
| enumwims | 枚举后备 WIM 文件。 |
| queryfile | 查询文件是否由 WIM 支持，如果是，则显示有关 WIM 文件的详细信息。 |
| `<filename>` | 指定文件名。 |
| removewim | 从备份文件中删除 WIM。 |

### <a name="examples"></a>示例

要从数据源0枚举驱动器 C：的文件，请键入：

```
fsutil wim enumfiles C: 0
```

若要枚举驱动器 C：的后备 WIM 文件，请键入：

```
fsutil wim enumwims C:
```

若要查看某个文件是否由 WIM 支持，请键入：

```
fsutil wim C:\Windows\Notepad.exe
```

若要从卷 C：和数据源2的备份文件中删除 WIM，请键入：

```
fsutil wim removewims C: 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
