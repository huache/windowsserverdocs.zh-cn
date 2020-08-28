---
title: mklink
description: 用于创建目录或文件符号或硬链接的 mklink 命令的参考文章。
ms.topic: reference
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 13d842dcad62392fa36dc705233f292b7aa1d48f
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037815"
---
# <a name="mklink"></a>mklink

创建目录或文件符号或硬链接。

## <a name="syntax"></a>语法

```
mklink [[/d] | [/h] | [/j]] <link> <target>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /d | 创建目录符号链接。 默认情况下，此命令将创建文件符号链接。 |
| /h | 创建硬链接，而不是符号链接。 |
| /j | 创建目录连接。 |
| `<link>` | 指定正在创建的符号链接的名称。 |
| `<target>` | 指定新符号链接引用的路径 (相对或绝对) 。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要创建和删除名为、MyFolder 和 Myfile.txt 的符号链接，请从根目录到 \Users\User1\Documents 目录，并在该目录中键入：

```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [del 命令](del.md)

- [rd 命令](rd.md)

- [Windows PowerShell 中的新项](/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
