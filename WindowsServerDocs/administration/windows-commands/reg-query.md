---
title: reg query
description: Reg query 命令的参考文章，它返回位于注册表中指定子项下的子项和条目的列表。
ms.topic: reference
ms.assetid: 0e6a0d7c-ed9b-4318-833d-33f265a81f39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 633928d89059e1b9a9677141011b391ee0d34757
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025081"
---
# <a name="reg-query"></a>reg query

返回位于注册表中指定子项下的子子项和条目的列表。

## <a name="syntax"></a>语法

```
reg query <keyname> [{/v <Valuename> | /ve}] [/s] [/se <separator>] [/f <data>] [{/k | /d}] [/c] [/e] [/t <Type>] [/z]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname>` | 指定子项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /v `<Valuename>` | 指定要查询的注册表值名称。 如果省略，则返回 *keyname* 的所有值名称。 如果也使用了 **/f**选项，则此参数的*Valuename*是可选的。 |
| /ve | 为空值名称运行查询。 |
| /s | 指定以递归方式查询所有子项和值名称。 |
| /se `<separator>` | 指定要在值名称类型 **REG_MULTI_SZ**中搜索的单个值分隔符。 如果未指定 *separator* ，则使用 **\ 0** 。 |
| /f `<data>` | 指定要搜索的数据或模式。 如果字符串包含空格，请使用双引号。 如果未指定，则使用通配符 (**&#42;**) 作为搜索模式。 |
| 遇到 | 指定仅在项名称中搜索。 |
| /d | 指定仅搜索数据。 |
| /c | 指定查询区分大小写。 默认情况下，查询不区分大小写。 |
| /e | 指定仅返回完全匹配项。 默认情况下，将返回所有匹配项。 |
| /t `<Type>` | 指定要搜索的注册表类型。 有效类型为： **REG_SZ**、 **REG_MULTI_SZ**、 **REG_EXPAND_SZ**、 **REG_DWORD**、 **REG_BINARY**、 **REG_NONE**。 如果未指定，则搜索所有类型。 |
| /z | 指定在搜索结果中包含注册表类型的等价数值。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- **Reg 查询**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要在 HKLM\Software\Microsoft\ResKit 项中显示 name 值版本的值，请键入：

```
reg query HKLM\Software\Microsoft\ResKit /v Version
```

若要在名为 ABC 的远程计算机上的 HKLM\Software\Microsoft\ResKit\Nt\Setup 项下显示所有子项和值，请键入：

```
reg query \\ABC\HKLM\Software\Microsoft\ResKit\Nt\Setup /s
```

若要使用作为分隔符显示 REG_MULTI_SZ 类型的所有子项和值 **#** ，请键入：

```
reg query HKLM\Software\Microsoft\ResKit\Nt\Setup /se #
```

若要在数据类型 REG_SZ 的 HKLM 根下显示与系统区分大小写的键、值和数据，请键入：

```
reg query HKLM /f SYSTEM /t REG_SZ /c /e
```

若要在数据类型 REG_BINARY 的 HKCU 根键下显示与 **0F** 匹配的键、值和数据，请键入：

```
reg query HKCU /f 0F /d /t REG_BINARY
```

若要在 HKLM\SOFTWARE 下显示 null (默认) 的值名称和数据，请键入：

```
reg query HKLM\SOFTWARE /ve
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
