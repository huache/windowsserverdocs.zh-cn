---
title: pushd
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 396bc545-0f41-473e-b0ac-76fbbb74d390
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e7866a54e83bd57c8689512a1b75b151f74cb93c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837090"
---
# <a name="pushd"></a>pushd



存储用于**popd**命令的当前目录，然后更改为指定的目录。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
pushd [<Path>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<路径 >|指定要生成当前目录的目录。 此命令支持相对路径。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   每次使用**pushd**命令时，将存储一个目录供你使用。 但是，可以多次使用**pushd**命令来存储多个目录。

    目录按顺序存储在虚拟堆栈中。 如果使用**pushd**命令一次，则使用命令的目录将置于堆栈的底部。 如果再次使用该命令，第二个目录将置于第一个目录的顶部。 每次使用**pushd**命令时都会重复此过程。

    可以使用**popd**命令将当前目录更改为**pushd**命令最近存储的目录。 如果使用**popd**命令，堆栈顶部的目录将从堆栈中删除，当前目录将更改为该目录。 如果再次使用**popd**命令，将删除堆栈上的下一个目录。
-   如果启用了命令扩展， **pushd**命令将接受网络路径或本地驱动器号和路径。
-   如果指定网络路径， **pushd**命令会暂时分配最高的未使用的驱动器号（以 Z：）到指定的网络资源。 然后，该命令将当前驱动器和目录更改为新分配的驱动器上的指定目录。 如果在启用了命令扩展的情况下使用**popd**命令， **popd**命令将删除**pushd**创建的驱动器号分配。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例演示如何在批处理程序中使用**pushd**命令和**popd**命令，以更改运行批处理程序的目录，然后将其更改回：
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

[Popd](popd.md)