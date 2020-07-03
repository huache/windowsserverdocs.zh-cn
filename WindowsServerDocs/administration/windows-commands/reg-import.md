---
title: reg import
description: Reg import 命令的参考文章，它将包含已导出注册表子项、条目和值的文件的内容复制到本地计算机的注册表中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 77c8284dd2341f37292afdfd810b2182686aad68
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931866"
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
| `<filename>` | 指定包含要复制到本地计算机的注册表中的内容的文件的名称和路径。 必须使用**reg export**提前创建此文件。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Reg import**操作的返回值为：

    | 值 | 描述 |
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
