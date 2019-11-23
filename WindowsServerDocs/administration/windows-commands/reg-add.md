---
title: reg 添加
description: '适用于 * * * * 的 Windows 命令主题 '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9ad143e-dc10-4e2e-a229-408393c40079
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b478ce0c98ec77f1387d8f894364f53cf8d2142
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371760"
---
# <a name="reg-add"></a>reg 添加


向注册表中添加新的子项或条目。

## <a name="syntax"></a>语法

```
reg add <KeyName> [{/v ValueName | /ve}] [/t DataType] [/s Separator] [/d Data] [/f]
```
有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="parameters"></a>参数

|      参数      |                                                                                                                                                                                                                                                                   描述                                                                                                                                                                                                                                                                   |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \<KeyName<em>></em> | 指定要添加的子项或项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\\<ComputerName >\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
|   /v \<ValueName >   |                                                                                                                                                                                                                                指定要添加到指定子项下的注册表项的名称。                                                                                                                                                                                                                                 |
|         /ve         |                                                                                                                                                                                                                                指定添加到注册表中的注册表项的值为 null。                                                                                                                                                                                                                                |
|     /t \<类型 >      |                                                                                                                                          指定注册表项的类型。 *类型*必须为以下类型之一：</br>REG_SZ</br>REG_MULTI_SZ</br>REG_DWORD_BIG_ENDIAN</br>REG_DWORD</br>REG_BINARY</br>REG_DWORD_LITTLE_ENDIAN</br>REG_LINK</br>REG_FULL_RESOURCE_DESCRIPTOR</br>REG_EXPAND_SZ                                                                                                                                          |
|   /s \<分隔符 >   |                                                                                                                                                              指定在指定了 REG_MULTI_SZ 数据类型并且需要列出多个条目时用于分隔多个数据实例的字符。 如果未指定，则默认分隔符为 **\ 0**。                                                                                                                                                              |
|     /d \<数据 >      |                                                                                                                                                                                                                                                 指定新注册表项的数据。                                                                                                                                                                                                                                                  |
|         /f          |                                                                                                                                                                                                                                           在不提示确认的情况下添加注册表项。                                                                                                                                                                                                                                           |
|         /?          |                                                                                                                                                                                                                                              在命令提示符下显示**reg add**帮助。                                                                                                                                                                                                                                               |

## <a name="remarks"></a>备注

-   此操作无法添加子树。 此版本的**reg**不要求在添加子项时进行确认。
-   下表列出了**reg add**操作的返回值。

| 值 | 描述 |
|-------|-------------|
|   0   |   成功   |
|   1   |   失败   |

-   对于 REG_EXPAND_SZ 密钥类型，请在/d 参数内使用带有 **%** "的插入符号（ **^** ）

## <a name="BKMK_examples"></a>示例

若要在远程计算机 ABC 上添加密钥 HKLM\Software\MyCo，请键入：
```
REG ADD \\ABC\HKLM\Software\MyCo
```
若要将注册表项添加到 HKLM\Software\MyCo，并将其值指定为类型为**data** REG_BINARY 和**fe340ead**的数据，请键入：
```
REG ADD HKLM\Software\MyCo /v Data /t REG_BINARY /d fe340ead
```
若要将多值注册表项添加到 HKLM\Software\MyCo，其值名称为**MRU**类型 REG_MULTI_SZ 和数据**fax\0mail\0\0**，请键入：
```
REG ADD HKLM\Software\MyCo /v MRU /t REG_MULTI_SZ /d fax\0mail\0\0
```
若要将扩展的注册表项添加到 HKLM\Software\MyCo，其值名称为 REG_EXPAND_SZ 类型为**路径**且值为 **% systemroot%** 的数据，请键入：
```
REG ADD HKLM\Software\MyCo /v Path /t REG_EXPAND_SZ /d ^%systemroot^%
```

#### <a name="additional-references"></a>其他参考

[命令行语法项](command-line-syntax-key.md)
