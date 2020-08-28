---
title: pushd
description: Pushd 命令的参考文章，其中存储了用于 popd 命令的当前目录，然后更改为指定的目录。
ms.topic: reference
ms.assetid: 396bc545-0f41-473e-b0ac-76fbbb74d390
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 383f3f6da4fc171629350eaa9257ffe9759cca8e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033795"
---
# <a name="pushd"></a>pushd

存储用于 **popd** 命令的当前目录，然后更改为指定的目录。

每次使用 **pushd** 命令时，将存储一个目录供你使用。 但是，可以多次使用 **pushd** 命令来存储多个目录。 目录按顺序存储在虚拟堆栈中，因此，如果你使用 **pushd** 命令一次，则使用命令的目录将放置在堆栈的底部。 如果再次使用该命令，第二个目录将置于第一个目录的顶部。 每次使用 **pushd** 命令时都会重复此过程。

如果使用 **popd** 命令，则会删除堆栈顶部的目录，并将当前目录更改为该目录。 如果再次使用 **popd** 命令，将删除堆栈上的下一个目录。 如果启用了命令扩展，则 **popd** 命令将删除由 **pushd** 命令创建的任何驱动器号 assignations。

## <a name="syntax"></a>语法

```
pushd [<path>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<path>` | 指定要生成当前目录的目录。 此命令支持相对路径。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 如果启用了命令扩展， **pushd** 命令将接受网络路径或本地驱动器号和路径。

- 如果指定网络路径， **pushd** 命令会暂时将从 Z： ) 开始 (最高的未使用的驱动器号分配给指定的网络资源。 然后，该命令将当前驱动器和目录更改为新分配的驱动器上的指定目录。 如果在启用了命令扩展的情况下使用 **popd** 命令， **popd** 命令将删除 **pushd**创建的驱动器号分配。

### <a name="examples"></a>示例

若要更改运行批处理程序的当前目录，然后将其更改回：

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

- [popd 命令](popd.md)
