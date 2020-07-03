---
title: writer
description: 编写器的参考文章，用于验证是否包括了写入器或组件，或者从备份或还原过程中排除了写入器或组件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7cf98295-411d-4705-8573-f898ff45c140
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 16746f2f070b87e0c287f3a49b19a480ba5399c9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936095"
---
# <a name="writer"></a>writer



验证是否包括了写入器或组件，或者是否从备份或还原过程中排除了写入器或组件。 如果在没有参数的情况下使用，则**编写器**会在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
writer verify [<Writer> | <Component>]
writer exclude [<Writer> | <Component>]
```

### <a name="parameters"></a>参数

| 参数  |                                                                                      说明                                                                                      |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   验证   | 验证指定的编写器或组件是否包含在备份或还原过程中。 如果未包括写入器或组件，备份或还原过程将失败。 |
|  排除   |                                                   从备份或还原过程中排除指定的编写器或组件。                                                    |
| [\<Writer> |                                                                                     <Component>]                                                                                      |

## <a name="examples"></a>示例

若要通过指定写入器的 GUID 来验证写入器（对于此示例，为4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f），请键入：
```
writer verify {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
```
若要排除名称为系统编写器的编写器，请键入：
```
writer exclude System Writer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)