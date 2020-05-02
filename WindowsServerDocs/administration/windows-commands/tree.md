---
title: 树
description: 树的参考主题，用于显示路径的目录结构，或以图形方式显示驱动器中磁盘的目录结构。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 345d3192-401e-4a3b-a8ac-36a85c7be79d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 94b0429dadc3965c7e41ad5aa881fc902988ec9b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721276"
---
# <a name="tree"></a>树

以图形方式显示驱动器路径或磁盘的目录结构。



## <a name="syntax"></a>语法

```
tree [<Drive>:][<Path>] [/f] [/a]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器>：|指定包含要显示其目录结构的磁盘的驱动器。|
|\<路径>|指定要显示其目录结构的目录。|
|/f|显示每个目录中的文件的名称。|
|/a|指定**树**将使用文本字符而不是图形字符来显示链接子目录的行。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

**树**显示的结构取决于你在命令提示符处指定的参数。 如果未指定驱动器或路径，**树**将显示从当前驱动器的当前目录开始的树状结构。

## <a name="examples"></a>示例

若要显示当前驱动器中磁盘上所有子目录的名称，请键入：
```
tree \
```
若要每次显示一个屏幕，驱动器 C 上的所有目录中的文件，请键入：
```
tree c:\ /f | more 
```
若要在驱动器 C 上打印所有目录的列表，请键入：
```
tree c:\ /f  prn 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)