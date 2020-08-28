---
title: fsutil sparse
description: 用于管理稀疏文件的 fsutil sparse 命令的参考文章。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 77545920-2d13-4f35-a4d1-14dbec8340dc
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 50b8fb1428de955b38d2f6e3a059046d7f670558
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032995"
---
# <a name="fsutil-sparse"></a>fsutil sparse

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

管理稀疏文件。 稀疏文件是一个文件，其中包含一个或多个未分配的数据区域。

程序会将这些未分配的区域视为包含值为零的字节，并且没有磁盘空间表示这些零。 读取稀疏文件时，分配的数据将按存储的方式返回，且默认情况下，未分配的数据将根据 C2 安全要求规范返回零。 稀疏文件支持允许将数据从文件中的任何位置解除分配。

## <a name="syntax"></a>语法

```
fsutil sparse [queryflag] <filename>
fsutil sparse [queryrange] <filename>
fsutil sparse [setflag] <filename>
fsutil sparse [setrange] <filename> <beginningoffset> <length>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| queryflag | 查询稀疏。 |
| queryrange | 扫描文件并搜索可能包含非零数据的范围。 |
| setflag | 将所指示的文件标记为稀疏。 |
| setrange | 使用零填充文件的指定范围。 |
| `<filename>` | 指定文件的完整路径，包括文件名和扩展名，例如 *C:\documents\filename.txt*。 |
| `<beginningoffset>` | 指定文件中的偏移量，以将其标记为稀疏。 |
| `<length>` | 指定文件中要标记为稀疏 (的区域的长度) 以字节为单位）。 |

#### <a name="remarks"></a>注解

- 所有有意义或非零的数据都将被分配，而所有无意义的数据 (由零组成的大型数据字符串) 未分配。

- 在稀疏文件中，大范围的零可能不需要磁盘分配。 在写入文件时，将根据需要分配非零数据的空间。

- 只有压缩文件或稀疏文件才能有操作系统已知的零范围。

- 如果文件是稀疏文件或压缩文件，NTFS 可能会释放文件中的磁盘空间。 这会将字节范围设置为零，而不会扩展文件大小。

### <a name="examples"></a>示例

若要将名为 *sample.txt* *的文件作为稀疏目录标记* ，请键入：

```
fsutil sparse setflag c:\temp\sample.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
