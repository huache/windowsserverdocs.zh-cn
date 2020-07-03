---
title: popd
description: Pnputil 命令的参考文章，此命令将当前目录更改为 pushd 命令最近存储的目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a4c52d5-9fd1-4eac-9c0c-5767b25728ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 002a0d84770738db2b00bedcd1e01df3b1b61b76
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937005"
---
# <a name="popd"></a>popd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

**Popd**命令将当前目录更改为**pushd**命令最近存储的目录。

每次使用**pushd**命令时，将存储一个目录供你使用。 但是，可以多次使用**pushd**命令来存储多个目录。 目录按顺序存储在虚拟堆栈中，因此，如果你使用**pushd**命令一次，则使用命令的目录将放置在堆栈的底部。 如果再次使用该命令，第二个目录将置于第一个目录的顶部。 每次使用**pushd**命令时都会重复此过程。

如果使用**popd**命令，则会删除堆栈顶部的目录，并将当前目录更改为该目录。 如果再次使用**popd**命令，将删除堆栈上的下一个目录。 如果启用了命令扩展，则**popd**命令将删除由**pushd**命令创建的任何驱动器号 assignations。

## <a name="syntax"></a>语法

```
popd
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要更改运行批处理程序的当前目录，然后将其更改回，请键入：

```
@echo off
rem This batch file deletes all .txt files in a specified directory
pushd %1
del *.txt
popd
cls
echo All text files deleted in the %1 directory
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [pushd](pushd.md)
