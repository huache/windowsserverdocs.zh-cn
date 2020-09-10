---
title: ftp mls
description: Ftp mls 命令的参考文章，其中显示远程目录中的文件和子目录的简短列表。
ms.topic: reference
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b46e3fdd525676eb99ddc25d771027508f02f678
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635351"
---
# <a name="ftp-mls"></a>ftp mls

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程目录中的文件和子目录的简短列表。

## <a name="syntax"></a>语法

```
mls <remotefile>[ ] <localfile>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要查看其列表的文件。 指定 *remotefiles*时，请使用连字符来表示远程计算机上的当前工作目录。 |
| `<localfile>` | 指定要在其中存储列表的本地文件。 指定 *localfile*时，请使用连字符在屏幕上显示列表。 |

### <a name="examples"></a>示例

若要显示 *dir1* 和 *dir2*的文件和子目录的缩略列表，请键入：

```
mls dir1 dir2 -
```

若要将 *dir1* 和 *dir2* 的文件和子目录的简短列表保存 *dirlist.txt*，请键入：

```
mls dir1 dir2 dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
