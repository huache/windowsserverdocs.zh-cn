---
title: reg copy
description: Reg copy 命令的参考文章，它将注册表项复制到本地或远程计算机上的指定位置。
ms.topic: reference
ms.assetid: 3fe74213-39ec-4b2d-ba3d-086243eac997
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a56f4d14c7dd52ba23f126c44ff940c694993377
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028065"
---
# <a name="reg-copy"></a>reg copy

将注册表项复制到本地或远程计算机上的指定位置。

## <a name="syntax"></a>语法

```
reg copy <keyname1> <keyname2> [/s] [/f]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname1>` | 指定要添加的子项或项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| `<keyname2>` | 指定要比较的第二个子键的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /s | 复制指定子项下的所有子项和项。 |
| /f | 复制子项，而不提示确认。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 此命令在复制子项时不要求确认。

- **Reg 比较**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要将项 MyApp 下的所有子项和值复制到 key SaveMyApp，请键入：

```
reg copy HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp /s
```

若要将名为天干/地支的计算机上的 MyCo 项下的所有值复制到当前计算机上的键 MyCo1，请键入：

```
reg copy \\ZODIAC\HKLM\Software\MyCo HKLM\Software\MyCo1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
