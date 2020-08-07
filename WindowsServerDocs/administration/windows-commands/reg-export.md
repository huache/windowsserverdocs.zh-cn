---
title: reg export
description: 用于将本地计算机的指定子项、项和值复制到文件中以传输到其他服务器的注册表导出命令的参考文章。
ms.topic: article
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 31f59aca51b74150682a5ba3085b7ffcef058d29
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884130"
---
# <a name="reg-export"></a>reg export

将本地计算机的指定子项、项和值复制到文件中，以便传输到其他服务器。

## <a name="syntax"></a>语法

```
reg export <keyname> <filename> [/y]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| `<keyname>` | 指定子项的完整路径。 导出操作仅适用于本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和**HKCC**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| `<filename>` | 指定要在操作过程中创建的文件的名称和路径。 文件必须具有 .reg 扩展名。 |
| /y | 用名称*文件名*覆盖任何现有文件，并且不提示确认。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Reg 导出**操作的返回值为：

    | 值 | 描述 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要将项 MyApp 的所有子项和值的内容导出到文件 AppBkUp，请键入：

```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
