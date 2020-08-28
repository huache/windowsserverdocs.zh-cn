---
title: fsutil reparsepoint
description: 用于查询或删除重新分析点的 fsutil reparsepoint 命令的参考文章。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: fb95c8ee-a418-4520-a12a-7754ae947c3c
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 94feb56f4c5ed590c87b20d475f4aefa7ba11dd4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037315"
---
# <a name="fsutil-reparsepoint"></a>fsutil reparsepoint

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

查询或删除重新分析点。  **Fsutil reparsepoint**命令通常由支持专业人员使用。

重新分析点是 NTFS 文件系统对象，这些对象具有可定义的属性，其中包含用户定义数据。 它们用于：

- 在 i/o) 子系统 (的输入/输出中扩展功能。

- 充当目录接合点和卷装入点。

- 将特定文件标记为特定于文件系统筛选器驱动程序。

## <a name="syntax"></a>语法

```
fsutil reparsepoint [query] <filename>
fsutil reparsepoint [delete] <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| query | 检索与指定句柄标识的文件或目录关联的重新分析点数据。 |
| delete | 从文件或目录中删除由指定句柄标识的重新分析点，但不删除文件或目录。 |
| `<filename>` | 指定文件的完整路径，包括文件名和扩展名，例如 *C:\documents\filename.txt*。 |

#### <a name="remarks"></a>注解

- 当程序设置重新分析点时，它将存储此数据以及一个重新分析标记，该标记可唯一地标识其存储的数据。 当文件系统使用重新分析点打开文件时，它会尝试查找关联的文件系统筛选器。 如果找到文件系统筛选器，筛选器将按重新分析数据的指示处理该文件。 如果找不到文件系统筛选器，则 **文件打开** 操作将失败。

### <a name="examples"></a>示例

若要检索与 *c:\server*关联的重新分析点数据，请键入：

```
fsutil reparsepoint query c:\server
```

若要从指定的文件或目录中删除重新分析点，请使用以下格式：

```
fsutil reparsepoint delete c:\server
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
