---
title: ftp mput
description: Ftp mput 命令的参考主题，它使用当前文件传输类型将本地文件复制到远程计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5006c1ba19f0e017dea377b47bd0d89a68266382
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820407"
---
# <a name="ftp-mput"></a>ftp mput

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。

## <a name="syntax"></a>语法

```
mput <localfile>[ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要复制到远程计算机的本地文件。 |

### <a name="examples"></a>示例

要使用当前文件传输类型将*Program1*和*program2.c*复制到远程计算机，请键入：

```
mput Program1.exe Program2.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
