---
title: ftp ls
description: Ftp ls 命令的参考文章，其中显示了远程计算机上的文件和子目录的缩略列表。
ms.topic: reference
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 845d8fed8dbb637a241d4b1c4491ef9f037eceb8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621610"
---
# <a name="ftp-ls"></a>ftp ls

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程计算机上的文件和子目录的缩写列表。

## <a name="syntax"></a>语法

```
ls [<remotedirectory>] [<localfile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| `[<remotedirectory>]` | 指定要查看其列表的目录。 如果未指定目录，则使用远程计算机上的当前工作目录。 |
| `[<localfile>]` | 指定要在其中存储列表的本地文件。 如果未指定本地文件，则结果将显示在屏幕上。 |

### <a name="examples"></a>示例

若要显示远程计算机上的文件和子目录的缩写列表，请键入：

```
ls
```

若要获取远程计算机上的 *dir1* 的缩略目录列表，并将其保存到名为 *dirlist.txt*的本地文件中，请键入：

```
ls dir1 dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
