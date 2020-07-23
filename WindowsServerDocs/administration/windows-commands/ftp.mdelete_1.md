---
title: ftp mdelete
description: Ftp mdelete 命令的参考文章，用于删除远程计算机上的文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0e763a1989ba820e4a4bb19842432368e17f1044
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957279"
---
# <a name="ftp-mdelete"></a>ftp mdelete

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除远程计算机上的文件。

## <a name="syntax"></a>语法
```
mdelete <remotefile>[...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要删除的远程文件。 |

### <a name="examples"></a>示例

若要删除*a.exe*和*b.exe*的远程文件，请键入：

```
mdelete a.exe b.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
