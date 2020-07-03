---
title: reg restore
description: Reg restore 命令的参考文章，它将已保存的子项和条目写入注册表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1483fc6998d7b286a81dc3cb1df021afb7e66650
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931041"
---
# <a name="reg-restore"></a>reg restore

将保存的子项和项写入注册表。

## <a name="syntax"></a>语法

```
reg restore <keyname> <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname>` | 指定要还原的子项的完整路径。 还原操作仅适用于本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和**HKCC**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| `<filename>` | 指定包含要写入注册表的内容的文件的名称和路径。 必须使用**reg save**命令提前创建此文件，并且该文件的扩展名必须为 hiv。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 在编辑任何注册表项之前，必须使用**reg save**命令保存父子项。 如果编辑失败，则可以使用**reg restore**操作还原原始子项。

- **注册表还原**操作的返回值为：

    | 值 | 描述 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要将名为 NTRKBkUp. hiv 的文件还原到密钥 HKLM\Software\Microsoft\ResKit，并覆盖该项的现有内容，请键入：

```
reg restore HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [reg save 命令](reg-save.md)
