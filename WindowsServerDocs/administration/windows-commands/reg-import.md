---
title: reg import
description: Reg import 命令的参考文章，它将包含已导出注册表子项、条目和值的文件的内容复制到本地计算机的注册表中。
ms.topic: reference
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 49f83a20b4f9c9e1e64f6e33f0980757de60d9ec
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627031"
---
# <a name="reg-import"></a>reg import

将包含导出的注册表子项、项和值的文件的内容复制到本地计算机的注册表中。

## <a name="syntax"></a>语法

```
reg import <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<filename>` | 指定包含要复制到本地计算机的注册表中的内容的文件的名称和路径。 必须使用 **reg export**提前创建此文件。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Reg import**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要从名为 AppBkUp 的文件中导入注册表项，请键入：

```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [reg export 命令](reg-export.md)
