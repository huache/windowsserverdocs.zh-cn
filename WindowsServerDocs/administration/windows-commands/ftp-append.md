---
title: ftp append
description: 使用 "当前文件类型" 设置将本地文件追加到远程计算机上的文件的 ftp append 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f1d1cf36139f00f3d61e400cb38960d2c8551532
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925163"
---
# <a name="ftp-append"></a>ftp append

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用 "当前文件类型" 设置将本地文件追加到远程计算机上的文件。

## <a name="syntax"></a>语法

```
append <localfile> [remotefile]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要添加的本地文件。 |
| [remotefile] | 指定远程计算机上添加的文件 <localfile> 。 如果不使用此参数，则 `<localfile>` 使用该名称代替远程文件名。 |

### <a name="examples"></a>示例

若要在远程计算机上追加*file2.txt* *file1.txt* ，请键入：

```
append file1.txt file2.txt
```

将本地*file1.txt*追加到远程计算机上名为*file1.txt*的文件。

```
append file1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
