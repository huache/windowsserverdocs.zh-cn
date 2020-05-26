---
title: ftp ls
description: Ftp ls 命令的参考主题，它显示远程计算机上的文件和子目录的缩写列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ae913f001c3ddffce9ff81c9c5c5fd32f436da5
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820167"
---
# <a name="ftp-ls"></a>ftp ls

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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

若要获取远程计算机上的*dir1*的缩写目录列表，并将其保存到名为*dirlist*的本地文件中，请键入：

```
ls dir1 dirlist.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
