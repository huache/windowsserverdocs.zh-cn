---
title: Md
description: '适用于 * * * * 的 Windows 命令主题 '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3751b185677bfee9d0519b9a617bea1df063c1e7
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259072"
---
# <a name="md"></a>Md



创建目录或子目录。

> [!NOTE]
> 此命令与**mkdir**命令相同。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
md [<Drive>:]<Path>
mkdir [<Drive>:]<Path>
```

## <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器 >：|指定要在其上创建新目录的驱动器。|
|\<路径 >|必须的。 指定新目录的名称和位置。 任何单个路径的最大长度由文件系统确定。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

默认情况下启用的命令扩展允许你使用单个**md**命令在指定路径中创建中间目录。

## <a name="BKMK_examples"></a>示例

若要在当前目录中创建名为 Directory1 的目录，请键入：
```
md Directory1
```
若要在启用了命令扩展的情况下在根目录中创建目录树 Taxes\Property\Current，请键入：
```
md \Taxes\Property\Current
```
如前面的示例所示，若要在根目录中创建目录树 Taxes\Property\Current，但禁用了命令扩展，请键入以下命令序列：
```
md \Taxes
md \Taxes\Property
md \Taxes\Property\Current
```

#### <a name="additional-references"></a>其他参考

[命令行语法项](command-line-syntax-key.md)

[Cmd](cmd.md)