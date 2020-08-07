---
title: reg add
description: Reg add 命令的参考文章，其中向注册表中添加了一个新的子项或条目。
ms.topic: article
ms.assetid: d9ad143e-dc10-4e2e-a229-408393c40079
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 549c9e4ff0eb09e051debdee12003031a8443e18
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884208"
---
# <a name="reg-add"></a>reg add

向注册表中添加新的子项或条目。

## <a name="syntax"></a>语法

```
reg add <keyname> [{/v Valuename | /ve}] [/t datatype] [/s Separator] [/d Data] [/f]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| `<keyname>` | 指定要添加的子项或项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为*keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和**HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM**和**hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /v`<Valuename>` | 指定添加注册表项的名称。 |
| /ve | 指定所添加的注册表项的值为 null。 |
| /t`<Type>` | 指定注册表项的类型。 *类型*必须为以下类型之一：<ul><li>REG_SZ</li><li>REG_MULTI_SZ</li><li>REG_DWORD_BIG_ENDIAN</li><li>REG_DWORD</li><li>REG_BINARY</li><li>REG_DWORD_LITTLE_ENDIAN</li><li>REG_LINK</li><li>REG_FULL_RESOURCE_DESCRIPTOR</li><li>REG_EXPAND_SZ</li></ul> |
| /s`<Separator>` | 指定在指定了**REG_MULTI_SZ**数据类型并且列出了多个条目时用于分隔多个数据实例的字符。 如果未指定，则默认分隔符为**\ 0**。 |
| /d`<Data>` | 指定新注册表项的数据。 |
| /f | 在不提示确认的情况下添加注册表项。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 此操作无法添加子树。 此版本的**reg**在添加子项时不要求确认。

- **Reg add**操作的返回值为：

| 值 | 描述 |
|--|--|
| 0 | 成功 |
| 1 | 失败 |

- 对于**REG_EXPAND_SZ**密钥类型，请在 **^** /d 参数内使用 ( ) 的脱字号 **%** 。

### <a name="examples"></a>示例

若要在远程计算机*ABC*上添加密钥*HKLM\Software\MyCo* ，请键入：

```
reg add \\ABC\HKLM\Software\MyCo
```

若要使用名为*Data*的值将注册表项添加到*HKLM\Software\MyCo*中，请键入*REG_BINARY*和*fe340ead*的数据类型：

```
reg add HKLM\Software\MyCo /v Data /t REG_BINARY /d fe340ead
```

若要使用名为*MRU*的值将多值注册表项添加到*HKLM\Software\MyCo* ，请键入*REG_MULTI_SZ*和*fax\0mail\0\0*的数据类型：

```
reg add HKLM\Software\MyCo /v MRU /t REG_MULTI_SZ /d fax\0mail\0\0
```

若要将扩展的注册表项添加到*HKLM\Software\MyCo* ，并将其值命名为*Path*、类型*REG_EXPAND_SZ*和 *% systemroot%* 的数据，请键入：

```
reg add HKLM\Software\MyCo /v Path /t REG_EXPAND_SZ /d ^%systemroot^%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
