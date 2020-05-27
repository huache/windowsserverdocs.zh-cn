---
title: ftp mdir
description: Ftp mdir 命令的参考主题，其中显示远程目录中的文件和子目录的目录列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b192e6de23105fcc696d8369ce0280167a201e20
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820217"
---
# <a name="ftp-mdir"></a>ftp mdir

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程目录中的文件和子目录的目录列表。

## <a name="syntax"></a>语法

```
mdir <remotefile>[...] <localfile>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要查看其列表的目录或文件。 可以指定多个*remotefiles*。 键入连字符（-）以使用远程计算机上的当前工作目录。 |
| `<localfile>` | 指定用于存储列表的本地文件。 此参数是必需的。 键入连字符（-）以在屏幕上显示列表。 |

### <a name="examples"></a>示例

若要在屏幕上显示 " *dir1* " 和 " *dir2* " 的目录列表，请键入：

```
mdir dir1 dir2 -
```

若要在名为*dirlist*的本地文件中保存*dir1*和*dir2*的合并目录列表，请键入：

```
mdir dir1 dir2 dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
