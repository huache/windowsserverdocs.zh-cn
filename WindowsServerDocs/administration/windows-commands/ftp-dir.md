---
title: ftp dir
description: Ftp dir 命令的参考文章，其中显示了远程计算机上的目录文件和子目录的列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a29a92a5-7b79-4e6e-95cf-2ccb38bb6fb2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1234b11beb61027a8e56f713f76d2c2bdcc4618
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933149"
---
# <a name="ftp-dir"></a>ftp dir

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程计算机上的目录文件和子目录的列表。

## <a name="syntax"></a>语法

```
dir [<remotedirectory>] [<localfile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| `[<remotedirectory>]` | 指定要查看其列表的目录。 如果未指定目录，则使用远程计算机上的当前工作目录。 |
| `[<localfile>]` | 指定要在其中存储目录列表的本地文件。 如果未指定本地文件，则结果将显示在屏幕上。 |

### <a name="examples"></a>示例

若要在远程计算机上显示*dir1*的目录列表，请键入：

```
dir dir1
```

若要将远程计算机上的当前目录列表保存*dirlist.txt*本地文件，请键入：

```
dir . dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
