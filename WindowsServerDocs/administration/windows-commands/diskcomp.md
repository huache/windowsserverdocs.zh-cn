---
title: diskcomp
description: Diskcomp 命令的参考文章，用于比较两个软盘的内容。
ms.topic: article
ms.assetid: 4f56f534-a356-4daa-8b4f-38e089341e42
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 71401942f25d3f503639b2931f2f0ee49229e15b
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890972"
---
# <a name="diskcomp"></a>diskcomp

比较两个软盘的内容。 如果在没有参数的情况下使用，则**diskcomp**将使用当前驱动器来比较两个磁盘。

## <a name="syntax"></a>语法

```
diskcomp [<drive1>: [<drive2>:]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<drive1>` | 指定包含其中一张软盘的驱动器。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Diskcomp**命令仅适用于软盘。 不能将**diskcomp**用于硬盘。 如果为*drive1*或*drive2*指定硬盘驱动器，则**diskcomp**将显示以下错误消息：

  ```
  Invalid drive specification
  Specified drive does not exist
  or is nonremovable
  ```

- 如果要进行比较的两个磁盘上的所有磁道都相同 (它将忽略磁盘的卷号) ， **diskcomp**将显示以下消息：

  ```
  Compare OK
  ```

  如果曲目不相同， **diskcomp**将显示类似于以下内容的消息：

  ```
  Compare error on
  side 1, track 2
  ```

  当**diskcomp**完成比较时，将显示以下消息：

  ```
  Compare another diskette (Y/N)?
  ```

  如果按 " **Y**"， **diskcomp**会提示您插入磁盘以进行下一次比较。 如果按**N**， **diskcomp**将停止比较。

- 如果省略*drive2*参数，则**diskcomp**将为*drive2*使用当前驱动器。 如果省略这两个驱动器参数，则**diskcomp**将使用当前驱动器。 如果当前驱动器与*drive1*相同，则**diskcomp**会提示你在必要时交换磁盘。

- 如果为*drive1*和*drive2*指定相同的软盘驱动器，则**diskcomp**将使用一个驱动器对它们进行比较，并根据需要提示插入磁盘。 可能需要多次交换磁盘，具体取决于磁盘容量和可用内存量。

- **Diskcomp**无法将单面磁盘与双面磁盘进行比较，也无法将高密度磁盘与双密度磁盘进行比较。 如果*drive1*中的磁盘与*drive2*中的磁盘不属于同一类型，则**diskcomp**将显示以下消息：

  ```
  Drive types or diskette types not compatible
  ```

- **Diskcomp**不适用于网络驱动器或由**subst**命令创建的驱动器。 如果尝试将**diskcomp**与任何这些类型的驱动器一起使用，则**diskcomp**将显示以下错误消息：

  ```
  Invalid drive specification
  ```

- 如果将**diskcomp**用于使用**copy**创建的磁盘，则**diskcomp**可能会显示类似于以下内容的消息：

  ```
  Compare error on
  side 0, track 0
  ```

  即使磁盘上的文件相同，也可能出现这种类型的错误。 尽管**复制**重复的信息，但不一定要将其放置在目标磁盘上的相同位置。

- **diskcomp**退出代码：

  | 退出代码 | 说明 |
  | --------- | ----------- |
  | 0 | 磁盘相同 |
  | 1 | 发现差异 |
  | 3 | 出现硬错误 |
  | 4 | 出现初始化错误 |

  若要处理**diskcomp**返回的退出代码，可以在批处理程序的**if**命令行中使用*ERRORLEVEL*环境变量。

## <a name="examples"></a>示例

如果计算机只有一个软盘驱动器 (例如，驱动器 A) 并且要比较两个磁盘，请键入：

```
diskcomp a: a:
```

**Diskcomp**会根据需要提示插入每个磁盘。

为了说明如何**处理在 diskcomp 命令行**上使用*ERRORLEVEL*环境变量的批处理程序中的**diskcomp**退出代码：

```
rem Checkout.bat compares the disks in drive A and B
echo off
diskcomp a: b:
if errorlevel 4 goto ini_error
if errorlevel 3 goto hard_error
if errorlevel 1 goto no_compare
if errorlevel 0 goto compare_ok
:ini_error
echo ERROR: Insufficient memory or command invalid
goto exit
:hard_error
echo ERROR: An irrecoverable error occurred
goto exit
:break
echo You just pressed CTRL+C to stop the comparison
goto exit
:no_compare
echo Disks are not the same
goto exit
:compare_ok
echo The comparison was successful; the disks are the same
goto exit
:exit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
