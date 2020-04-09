---
title: move
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fde290a8-d385-450f-8987-ee837fed667d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: efd0cd0716c564a9570647820056ab9c38e41274
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839370"
---
# <a name="move"></a>move



将一个或多个文件从一个目录移动到另一个目录。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
move [{/y | /-y}] [<Source>] [<Target>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/y|禁止提示您确认是否要覆盖现有目标文件。|
|/-y|导致提示您确认是否要覆盖现有的目标文件。|
|\<源 >|指定要移动的文件的路径和名称。 如果要移动或重命名某个目录，则*源*应为当前目录路径和名称。|
|\<目标 >|指定要将文件移动到的路径和名称。 如果要移动或重命名目录，*目标*应该是所需的目录路径和名称。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   可以在 COPYCMD 环境变量中预设 **/y**命令行选项。 您可以在命令行上用 **/-y**替代此参数。 除非从批处理脚本内运行**复制**命令，否则默认值为在覆盖文件之前提示。
-   将加密文件移动到不支持加密文件系统（EFS）的卷会导致错误。 首先对文件进行解密，或将文件移动到支持 EFS 的卷。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将 \Data 目录中扩展名为 .xls 的所有文件移动到 \ Second_Q \Reports 目录，请键入：
```
move \data\*.xls \second_q\reports\ 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)