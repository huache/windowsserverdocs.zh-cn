---
title: reg compare
description: 用于比较指定注册表子项或项的 "reg compare" 命令的参考文章。
ms.topic: reference
ms.assetid: 177dc6a3-034e-4846-a394-330d03c14e0b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 51c385b9a051574602c2508b8efd8f657c62ec7c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627090"
---
# <a name="reg-compare"></a>reg compare

比较指定的注册表子项或条目。

## <a name="syntax"></a>语法

```
reg compare <keyname1> <keyname2> [{/v Valuename | /ve}] [{/oa | /od | /os | on}] [/s]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname1>` | 指定要添加的子项或项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| `<keyname2>` | 指定要比较的第二个子键的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 仅在 *keyname2* 中指定计算机名称会导致操作使用 *keyname1*中指定子项的路径。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /v `<Valuename>` | 指定要在子项下比较的值的名称。 |
| /ve | 指定只应比较值为 null 的项。 |
| /oa | 指定显示所有差异和匹配项。 默认情况下，仅列出差异。 |
| /od | 指定仅显示差异。 此选项为默认行为。 |
| /os | 指定仅显示匹配项。 默认情况下，仅列出差异。 |
| /on | 指定不显示任何内容。 默认情况下，仅列出差异。 |
| /s | 递归比较所有子项和项。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Reg 比较**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 比较成功，结果相同。 |
    | 1 | 比较失败。 |
    | 2 | 比较成功，发现差异。 |

- 结果中显示的符号包括：

    | 符号 | 说明 |
    |--|--|
    | = | *KeyName1* 数据等于 *KeyName2* 数据。 |
    | < | *KeyName1* 数据小于 *KeyName2* 数据。 |
    | > | *KeyName1* 数据大于 *KeyName2* 数据。 |

### <a name="examples"></a>示例

若要将 key **MyApp** 下的所有值与 key **SaveMyApp**下的所有值进行比较，请键入：

```
reg compare HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp
```

要比较 key **MyCo** 下的版本值和密钥 **MyCo1**下的版本值，请键入：

```
reg compare HKLM\Software\MyCo HKLM\Software\MyCo1 /v Version
```

若要比较名为天干/地支的计算机上 HKLM\Software\MyCo 下的所有子项和值，并在本地计算机上的 HKLM\Software\MyCo 下包含所有子项和值，请键入：

```
reg compare \\ZODIAC\HKLM\Software\MyCo \\. /s
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
