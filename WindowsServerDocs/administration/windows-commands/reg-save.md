---
title: reg save
description: Reg save 命令的参考文章，用于在指定的文件中保存指定子项、条目和注册表值的副本。
ms.topic: reference
ms.assetid: b326482b-c8af-467d-a20c-0481eeda3d5c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17c1bd3439d98ee2e0aa64cb3000f94dfbab41f4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025001"
---
# <a name="reg-save"></a>reg save

在指定的文件中保存指定子项、项和注册表值的副本。

## <a name="syntax"></a>语法

```
reg save <keyname> <filename> [/y]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname>` | 指定子项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| `<filename>` | 指定创建的文件的名称和路径。 如果未指定路径，则使用当前路径。 |
| /y | 使用名称 *文件名* 覆盖现有文件，而不提示确认。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 在编辑任何注册表项之前，必须使用 **reg save** 命令保存父子项。 如果编辑失败，则可以使用 **reg restore** 操作还原原始子项。

- **Reg save**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

要将 hive MyApp 保存到当前文件夹中作为名为 AppBkUp 的文件，请键入：

```
reg save HKLM\Software\MyCo\MyApp AppBkUp.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [reg restore 命令](reg-restore.md)