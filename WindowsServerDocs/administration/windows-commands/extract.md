---
title: extract
description: 用于从源位置提取文件的 "提取" 命令的参考文章。
ms.topic: article
ms.assetid: 20dab03e-f6e1-4eb8-b8a1-fd6f1d97ee83
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 130f9ee22e0603deaa50dfde267df1c39342e38c
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890372"
---
# <a name="extract"></a>extract

从 cabinet 或源提取文件。

## <a name="syntax"></a>语法

```
extract [/y] [/a] [/d | /e] [/l dir] cabinet [filename ...]
extract [/y] source [newname]
extract [/y] /c source destination
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 程序包 | 如果要提取两个或更多文件，请使用。 |
| filename | 要从 cab 文件中提取的文件的名称。 通配符和多个文件名 (用空白分隔) 可供使用。 |
| source | 压缩文件 (仅包含一个文件) 的 cabinet 文件。 |
| newname | 用于为提取的文件指定的新文件名。 如果未提供，则使用原始名称。 |
| /a | 处理所有 cabinet。 从前面提到的第一个 cabinet 开始，遵循 cabinet 链。 |
| /c | 将源文件复制到目标 (，从 DMF 磁盘复制) 。 |
| /d | 显示 cabinet 目录 (与 filename 一起使用以避免提取) 。 |
| /e | 提取 (使用而不是 *。* ) 提取所有文件。 |
| /l dir | 要放置解压缩文件的位置 (默认为当前目录) 。 |
| /y | 请不要在覆盖现有文件之前进行提示。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
