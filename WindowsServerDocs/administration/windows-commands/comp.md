---
title: comp
description: 用于比较每个文件或一组文件的内容的复合命令参考文章。
ms.topic: article
ms.assetid: 40319d23-704d-4da1-be93-8259547275d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 18bd39483957959c746913a4ee18014be40c9eaa
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880032"
---
# <a name="comp"></a>comp

逐字节比较两个文件或文件集的内容。 这些文件可以存储在同一驱动器上，也可以存储在不同的驱动器上，也可以存储在同一目录或不同的目录中。 此命令对文件进行比较时，会显示文件的位置和文件名。 如果在没有参数的情况下使用，则**comp**会提示你输入要比较的文件。

## <a name="syntax"></a>语法

```
comp [<data1>] [<data2>] [/d] [/a] [/l] [/n=<number>] [/c]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<data1>` | 指定要比较的第一个文件或一组文件的位置和名称。 您可以使用通配符 (**&#42;** 和 **？**) 来指定多个文件。 |
| `<data2>` | 指定要比较的第二个文件或一组文件的位置和名称。 您可以使用通配符 (**&#42;** 和 **？**) 来指定多个文件。 |
| /d | 以十进制格式显示差异。  (默认格式为十六进制。 )  |
| /a | 将差异显示为字符。 |
| /l | 显示出现差异的行号，而不是显示字节偏移量。 |
| /n =`<number>` | 仅比较为每个文件指定的行数，即使文件大小不同也是如此。 |
| /c | 执行不区分大小写的比较。 |
| /off [line] | 处理具有脱机属性集的文件。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

- 在比较过程中，"**复合**" 将显示用于标识文件之间不等信息位置的消息。 每条消息都表示不相等字节的偏移内存地址， (十六进制表示法内容，除非) 指定 **/a**或 **/d**命令行参数。 消息按以下格式显示：

    ```
    Compare error at OFFSET xxxxxxxx
    file1 = xx
    file2 = xx
    ```

    十个比较不相等后， **comp**将停止比较文件并显示以下消息：

    `10 Mismatches - ending compare`

- 如果省略*data1*或*data2*的必需组件，或者完全省略了*data2* ，则此命令将提示你输入缺少的信息。

- 如果*data1*只包含驱动器号或没有文件名的目录名称，则此命令会将指定目录中的所有文件与*data1*中指定的文件进行比较。

- 如果*data2*只包含驱动器号或目录名称，则*data2*的默认文件名将与*data1*的名称相同。

- 如果**comp**命令找不到指定的文件，它将提示你是否要比较其他文件。

- 你比较的文件可以具有相同的文件名，前提是它们位于不同的目录或不同的驱动器上。 您可以使用通配符 (**&#42;** 和 **？**) 指定文件名。

- 您必须指定 **/n**以比较不同大小的文件。 如果文件大小不同并且未指定 **/n** ，则显示以下消息：

    ```
    Files are different sizes
    Compare more files (Y/N)?
    ```

    若要比较这些文件，请按**N**停止命令。 然后，使用 **/n**选项再次比较每个文件的第一部分，再次运行**comp**命令。

- 如果使用通配符 (**&#42;** 和 **？**) 指定多个文件，则**comp**会找到与*data1*匹配的第一个文件，并将它与*data2*中的相应文件（如果存在）进行比较。 **Comp**命令报告与*data1*匹配的每个文件的比较结果。 完成后， **comp**显示以下消息：

    `Compare more files (Y/N)?`

    若要比较多个文件，请按**Y**。**Comp**命令会提示你输入新文件的位置和名称。 若要停止比较，请按**N**。当你按**Y**时，系统将提示你输入要使用的命令行选项。 如果未指定任何命令行选项，则**comp**将使用您之前指定的任何命令行选项。

## <a name="examples"></a>示例

若要将目录*c:\reports*的内容与备份目录进行比较 `\\sales\backup\april` ，请键入：

```
comp c:\reports \\sales\backup\april
```

若要比较*\invoice*目录中文本文件的前10行并以十进制格式显示结果，请键入：

```
comp \invoice\*.txt \invoice\backup\*.txt /n=10 /d
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)