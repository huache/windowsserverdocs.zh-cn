---
title: ftp mget
description: Ftp mget 命令的参考文章，其中使用当前文件传输类型将远程文件复制到本地计算机。
ms.topic: reference
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ca56e43df4a03fd52f8028d390cb2da62901ca06
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621620"
---
# <a name="ftp-mget"></a>ftp mget

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。

## <a name="syntax"></a>语法

```
mget <remotefile>[ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要复制到本地计算机的远程文件。 |

### <a name="examples"></a>示例

要使用当前文件传输类型将远程文件 *a.exe* 和 *b.exe* 复制到本地计算机，请键入：

```
mget a.exe b.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
