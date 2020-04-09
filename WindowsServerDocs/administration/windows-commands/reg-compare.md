---
title: 注册表比较
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 177dc6a3-034e-4846-a394-330d03c14e0b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 21eb459711f8ca72bf2f6d841d958bb25a96f845
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836540"
---
# <a name="reg-compare"></a>注册表比较



比较指定的注册表子项或条目。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
reg compare <KeyName1> <KeyName2> [{/v ValueName | /ve}] [{/oa | /od | /os | on}] [/s]
```

### <a name="parameters"></a>参数

|    参数    |                                                                                                                                                                                                                                                                                          说明                                                                                                                                                                                                                                                                                           |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   \<KeyName1 >   |                                                               指定要比较的第一个子项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。                                                                |
|   \<KeyName2 >   | 指定要比较的第二个子键的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 仅在*KeyName2*中指定计算机名称会导致操作使用*KeyName1*中指定子项的路径。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。 |
| /v \<ValueName > |                                                                                                                                                                                                                                                                     指定要在子项下比较的值的名称。                                                                                                                                                                                                                                                                      |
|       /ve       |                                                                                                                                                                                                                                                         指定只应比较值为 null 的项。                                                                                                                                                                                                                                                         |
|      [{/oa      |                                                                                                                                                                                                                                                                                              /od                                                                                                                                                                                                                                                                                               |
|       /oa       |                                                                                                                                                                                                                                             指定显示所有差异和匹配项。 默认情况下，仅列出差异。                                                                                                                                                                                                                                             |
|       /od       |                                                                                                                                                                                                                                                          指定仅显示差异。 这是默认行为。                                                                                                                                                                                                                                                          |
|       /os       |                                                                                                                                                                                                                                                    指定仅显示匹配项。 默认情况下，仅列出差异。                                                                                                                                                                                                                                                     |
|       /on       |                                                                                                                                                                                                                                                       指定不显示任何内容。 默认情况下，仅列出差异。                                                                                                                                                                                                                                                        |
|       /s        |                                                                                                                                                                                                                                                                         递归比较所有子项和项。                                                                                                                                                                                                                                                                          |
|       /?        |                                                                                                                                                                                                                                                                    在命令提示符下显示**reg 比较**的帮助。                                                                                                                                                                                                                                                                    |

## <a name="remarks"></a>备注

下表列出了**reg compare**的返回值。

|值|说明|
|-----|-----------|
|0|比较成功，结果相同。|
|1|比较失败。|
|2|比较成功，发现差异。|

下表列出了结果中显示的符号。

|符号|说明|
|------|-----------|
|=|*KeyName1*数据等于*KeyName2*数据。|
|<|*KeyName1*数据小于*KeyName2*数据。|
|>|*KeyName1*数据大于*KeyName2*数据。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将 key **MyApp**下的所有值与 key **SaveMyApp**下的所有值进行比较，请键入：

REG COMPARE HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp

要比较 key **MyCo**下的版本值和密钥**MyCo1**下的版本值，请键入：

REG COMPARE HKLM\Software\MyCo HKLM\Software\MyCo1/v 版本

若要将名为天干/地支的计算机上 HKLM\Software\MyCo 下的所有子项和值与本地计算机上 HKLM\Software\MyCo 下的所有子项和值进行比较，请键入：

.REG 比较 \\\\ZODIAC\HKLM\Software\MyCo \\\\。 /s

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)