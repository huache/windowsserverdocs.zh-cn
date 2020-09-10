---
title: regini
description: 用于从命令行或脚本修改注册表并应用在一个或多个文本文件中预设的更改的 regini.exe 命令的参考文章。
ms.topic: reference
ms.assetid: 5ff18dc3-5bd8-400a-b311-fd73a3267e8c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 78c56a68392d066047123dc77bafc3d1b01de127
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627477"
---
# <a name="regini"></a>regini

通过命令行或脚本修改注册表，并应用在一个或多个文本文件中预设的更改。 除了修改注册表项的权限外，还可以创建、修改或删除注册表项。

有关 regini.exe 用于更改注册表的文本脚本文件的格式和内容的详细信息，请参阅 [如何从命令行或脚本更改注册表值或权限](https://support.microsoft.com/help/264584/how-to-change-registry-values-or-permissions-from-a-command-line-or-a)。

## <a name="syntax"></a>语法

```
regini [-m \\machinename | -h hivefile hiveroot][-i n] [-o outputwidth][-b] textfiles...
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| -m `<\\computername>` | 指定包含要修改的注册表的远程计算机名称。 使用格式** \\ ComputerName**。 |
| -h `<hivefile hiveroot>` | 指定要修改的本地注册表配置单元。 必须以 **hivefile hiveroot**格式指定 hive 文件的名称和 hive 的根目录。 |
| -i `<n>` | 指定要用于指示命令输出中的注册表项树结构的缩进级别。 **regdmp.exe**工具 (以二进制格式获取注册表项的当前权限) 使用以四的倍数表示的缩进，因此默认值为**4**。 |
| -o `<outputwidth>` | 指定命令输出的宽度（以字符为限）。 如果输出将出现在 "命令" 窗口中，则默认值为窗口的宽度。 如果将输出定向到文件，则默认值为 **240** 个字符。 |
| -b | 指定 **regini.exe** 输出与以前的 **regini.exe**版本向后兼容。 |
| textfiles | 指定包含注册表数据的一个或多个文本文件的名称。 可以列出任意数目的 ANSI 或 Unicode 文本文件。 |

#### <a name="remarks"></a>备注

以下准则主要适用于包含使用 **regini.exe**应用的注册表数据的文本文件内容。

- 使用分号作为行尾注释字符。 它必须是行中的第一个非空白字符。

- 使用反斜杠指示行的继续符。 此命令将忽略反斜杠中的所有字符（最多 (，但不包括) 下一行的第一个非空白字符）。 如果在反斜杠之前包含多个空格，则会将其替换为单个空格。

- 使用硬制表符来控制缩进。 此缩进表示注册表项的树结构;但是，这些字符将转换为单个空格，而不考虑其位置。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
