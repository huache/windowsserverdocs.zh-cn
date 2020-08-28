---
title: ftp mls
description: Ftp mls 命令的参考文章，其中显示远程目录中的文件和子目录的简短列表。
ms.topic: reference
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b4eaf9a4b31fb233d281514bcc50ddc754d398a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038025"
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
