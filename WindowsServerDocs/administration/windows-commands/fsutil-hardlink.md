---
title: fsutil hardlink
description: 用于在现有文件和新文件之间创建硬链接的 "fsutil 硬链接" 命令参考文章。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 835fc6f1-cc84-4189-b29a-dde90792469e
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 9d3782736686106b892f3b35e74573e4e162ae80
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037355"
---
# <a name="fsutil-hardlink"></a>fsutil hardlink

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

在现有文件和新文件之间创建硬链接。 硬链接是文件的目录条目。 每个文件都可以被视为至少具有一个硬链接。

在 NTFS 卷上，每个文件都可以有多个硬链接，因此单个文件可以出现在多个目录中， (甚至) 不同名称的同一目录中。 由于所有链接都引用同一个文件，因此程序可以打开任何链接，并修改该文件。 仅在删除文件的所有链接后，才从文件系统中删除该文件。 创建硬链接后，程序可以像使用任何其他文件名一样使用它。

## <a name="syntax"></a>语法

```
fsutil hardlink create <newfilename> <existingfilename>
fsutil hardlink list <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| create | 在现有文件和新文件之间建立 NTFS 硬链接。  (NTFS 硬链接类似于 POSIX 硬链接。 )  |
| \<newfilename> | 指定要为其创建硬链接的文件。 |
| \<existingfilename> | 指定要从其创建硬链接的文件。 |
| list | 列出指向 *文件名*的硬链接。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
