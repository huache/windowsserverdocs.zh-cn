---
title: ftp recv
description: Ftp 接收命令的参考文章，它使用当前文件传输类型将远程文件复制到本地计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f249ce61-247d-421b-9b93-48bce5108800
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 01f9fc1d8e233d8e2c38f606dea12f5d342d5e44
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925785"
---
# <a name="ftp-recv"></a>ftp recv

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。

> [!NOTE]
> 此命令与[ftp get 命令](ftp-get.md)相同。

## <a name="syntax"></a>语法

```
recv <remotefile> [<localfile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要复制的远程文件。 |
| `[<localfile>]` | 指定要在本地计算机上使用的文件的名称。 如果未指定*localfile* ，则会为该文件提供*remotefile*的名称。 |

### <a name="examples"></a>示例

要使用当前文件传输将*test.txt*复制到本地计算机，请键入：

```
recv test.txt
```

要使用当前文件传输*test1.txt*将*test.txt*复制到本地计算机，请键入：

```
recv test.txt test1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp get 命令](ftp-get.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
