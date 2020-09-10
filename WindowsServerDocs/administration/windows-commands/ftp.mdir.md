---
title: ftp mdir
description: Ftp mdir 命令的参考文章，其中显示远程目录中的文件和子目录的目录列表。
ms.topic: reference
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 40c64d82f07a763dec3dd690780438eb2db35753
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636667"
---
# <a name="ftp-mdir"></a>ftp mdir

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程目录中的文件和子目录的目录列表。

## <a name="syntax"></a>语法

```
mdir <remotefile>[...] <localfile>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要查看其列表的目录或文件。 可以指定多个 *remotefiles*。 键入连字符 ( ) ，以便使用远程计算机上的当前工作目录。 |
| `<localfile>` | 指定用于存储列表的本地文件。 此参数是必需的。 键入连字符 (-) 以在屏幕上显示列表。 |

### <a name="examples"></a>示例

若要在屏幕上显示 " *dir1* " 和 " *dir2* " 的目录列表，请键入：

```
mdir dir1 dir2 -
```

若要在名为*dirlist.txt*的本地文件中保存*dir1*和*dir2*的合并目录列表，请键入：

```
mdir dir1 dir2 dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
