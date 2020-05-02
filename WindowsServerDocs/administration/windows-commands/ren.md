---
title: ren
description: 了解如何使用 ren 命令重命名文件或目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60398e12-a05d-4524-a73a-0a925943e21d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 21ce37795af3080245633938e96f891f7a485d53
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722420"
---
# <a name="ren"></a>ren

重命名文件或目录。 此命令与 "**重命名**" 命令相同。



## <a name="syntax"></a>语法

```
ren [<Drive>:][<Path>]<FileName1> <FileName2>
rename [<Drive>:][<Path>]<FileName1> <FileName2>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[\<驱动器>：][\<路径>]\<FileName1>|指定要重命名的文件或文件集的位置和名称。 *FileName1*可以包含通配符（**&#42;** 和 **？**）。|
|\<FileName2>|指定文件的新名称。 您可以使用通配符来指定多个文件的新名称。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

- 在重命名文件时，不能指定新的驱动器或路径。
- 不能使用**ren**命令在驱动器之间重命名文件，或将文件移动到不同的目录。
- 可以在*FileName*参数中使用通配符（**&#42;** 和 **？**）。 *FileName2*中由通配符表示的字符将与*FileName1*中的相应字符相同。
- *FileName2*必须是唯一的文件名。 如果*FileName2*与现有文件名相匹配，则**ren**会显示以下消息：  
  ```
  Duplicate file name or file not found
  ```

## <a name="examples"></a><a name="BKMK_examples"></a>示例

若要将当前目录中的所有 .txt 文件扩展名更改为 .doc 扩展名，请键入：
```
ren *.txt *.doc 
```
若要将目录的名称从 Chap10 更改为 Part10，请键入：
```
ren chap10 part10 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)