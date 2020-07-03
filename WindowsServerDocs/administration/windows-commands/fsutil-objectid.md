---
title: fsutil objectid
description: Fsutil objectid 命令的参考文章，它管理对象标识符以跟踪其他对象（如文件、目录和链接）。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 693ab895-9d0c-47c1-9f52-df5cd287842a
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 5ab0b95bdcde8bce51e1d5a2c14888229621fcaa
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925248"
---
# <a name="fsutil-objectid"></a>fsutil objectid

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

管理对象标识符（Oid），这是分布式链接跟踪（DLT）客户端服务和文件复制服务（FRS）使用的内部对象，用于跟踪其他对象（如文件、目录和链接）。 对象标识符在大多数程序中是不可见的，不应进行修改。

> [!WARNING]
> 请勿删除、设置或以其他方式修改对象标识符。 删除或设置对象标识符可能会导致文件的某些部分丢失数据，最多可包含整个数据量。 此外，可能会导致分布式链接跟踪（DLT）客户端服务和文件复制服务（FRS）出现不利的行为。

## <a name="syntax"></a>语法

```
fsutil objectid [create] <filename>
fsutil objectid [delete] <filename>
fsutil objectid [query] <filename>
fsutil objectid [set] <objectID> <birthvolumeID> <birthobjectID> <domainID> <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| create | 如果指定的文件尚不具有对象标识符，则创建一个。 如果文件已有对象标识符，则此子命令等效于**query**子命令。 |
| delete | 删除对象标识符。 |
| 查询 | 查询对象标识符。 |
| set | 设置对象标识符。 |
| `<objectID>` | 设置特定于文件的16字节十六进制标识符，该标识符在卷内保证是唯一的。 分布式链接跟踪（DLT）客户端服务和文件复制服务（FRS）使用该对象标识符来标识文件。 |
| `<birthvolumeID>` | 指示文件首次获得对象标识符时所在的卷。 此值是 DLT 客户端服务使用的16字节十六进制标识符。 |
| `<birthobjectID>` | 指示文件的原始对象标识符（移动文件时*objectID*可能会更改）。 此值是 DLT 客户端服务使用的16字节十六进制标识符。 |
| `<domainID>` | 16字节的十六进制域标识符。 当前未使用此值，因此必须将其设置为全零。 |
| `<filename>` | 指定文件的完整路径，包括文件名和扩展名，例如*C:\documents\filename.txt*。 |

#### <a name="remarks"></a>备注

- 具有对象标识符的任何文件也有一个出生卷标识符、一个出生对象标识符和一个域标识符。 移动文件时，对象标识符可能会改变，但出生卷和出生对象标识符保持不变。 此行为使 Windows 操作系统能够始终查找文件，无论该文件移动到何处。

### <a name="examples"></a>示例

若要创建对象标识符，请键入：

`fsutil objectid create c:\temp\sample.txt`

若要删除对象标识符，请键入：

`fsutil objectid delete c:\temp\sample.txt`

若要查询对象标识符，请键入：

`fsutil objectid query c:\temp\sample.txt`

若要设置对象标识符，请键入：

`fsutil objectid set 40dff02fc9b4d4118f120090273fa9fc f86ad6865fe8d21183910008c709d19e 40dff02fc9b4d4118f120090273fa9fc 00000000000000000000000000000000 c:\temp\sample.txt`

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
