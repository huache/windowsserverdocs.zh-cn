---
title: diskcopy
description: 有关 diskcopy 命令的参考文章，可将源驱动器中软盘的内容复制到目标驱动器中已格式化或未格式化的软盘。
ms.topic: article
ms.assetid: 5fd21efa-52cc-4e70-a7fe-35125a435106
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/07/2018
ms.openlocfilehash: b385d7fb371b0e33bcf16b240b051ce038a525a7
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890949"
---
# <a name="diskcopy"></a>diskcopy

将源驱动器中软盘的内容复制到目标驱动器中已格式化或未格式化的软盘。 如果在没有参数的情况下使用，则**diskcopy**使用源磁盘和目标磁盘的当前驱动器。

## <a name="syntax"></a>语法

```
diskcopy [<drive1>: [<drive2>:]] [/v]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<drive1>` | 指定包含源磁盘的驱动器。 |
| /v | 验证是否已正确复制信息。 此选项会降低复制过程的速度。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Diskcopy**仅适用于可移动磁盘，如软盘，它们必须是同一类型。 不能将**diskcopy**与硬盘一起使用。 如果为*drive1*或*drive2*指定硬盘驱动器，则**diskcopy**将显示以下错误消息：

    ```
    Invalid drive specification
    Specified drive does not exist or is nonremovable
    ```

    **Diskcopy**命令提示您插入源和目标磁盘，并等待您在键盘上按任意键，然后再继续。

    复制磁盘后， **diskcopy**会显示以下消息：

    ```
    Copy another diskette (Y/N)?
    ```

    如果按**Y**， **diskcopy**会提示您插入源磁盘和目标磁盘以进行下一次复制操作。 若要停止**diskcopy**进程，请按**N**。

    如果要复制到*drive2*中的未格式化软盘，则**diskcopy**会按照*drive1*中的磁盘上的相同面和扇区的数量来设置磁盘的格式。 **Diskcopy**在格式化磁盘和复制文件时显示以下消息：

    ```
    Formatting while copying
    ```

- 如果源磁盘具有卷序列号，则**diskcopy**将为目标磁盘创建新的卷序列号，并显示复制操作完成时的数字。

- 如果省略*drive2*参数，则**diskcopy**使用当前驱动器作为目标驱动器。 如果省略这两个驱动器参数，则**diskcopy**同时使用当前驱动器。 如果当前驱动器与*drive1*相同，则在必要时， **diskcopy**会提示你交换磁盘。

- 从软盘驱动器以外的驱动器（例如 C 驱动器）运行**diskcopy** 。 如果软盘*drive1*和软盘*drive2*相同，则**diskcopy**会提示你切换磁盘。 如果磁盘包含的信息超过可用内存可以容纳的数量，则**diskcopy**无法一次读取全部信息。 **Diskcopy**从源磁盘读取数据，将数据写入目标磁盘，并再次提示您插入源磁盘。 此过程将一直继续，直到复制了整个磁盘。

- 碎片是指磁盘上的现有文件之间存在未使用的磁盘空间的小区域。 零碎的源磁盘可能会减慢查找、读取或写入文件的进程。

    由于**diskcopy**在目标磁盘上生成源磁盘的完全相同的副本，因此源磁盘上的任何碎片都将传输到目标磁盘。 若要避免将碎片从一个磁盘传输到另一个磁盘，请使用[复制命令](copy.md)或[xcopy 命令](xcopy.md)复制磁盘。 由于**副本**和**xcopy**复制文件是连续的，因此不会对新磁盘进行分段。

    > [!NOTE]
    > 不能使用**xcopy**复制启动磁盘。

- **diskcopy**退出代码：

    | 退出代码 | 说明 |
    | --------- | ----------- |
    | 0 | 复制操作成功 |
    | 1 | 出现非致命读/写错误 |
    | 3 | 出现严重错误 |
    | 4 | 出现初始化错误 |

    若要处理**diskcomp**返回的退出代码，可以在批处理程序的**if**命令行中使用*ERRORLEVEL*环境变量。

## <a name="examples"></a>示例

若要将驱动器 B 中的磁盘复制到驱动器 A 中的磁盘，请键入：

```
diskcopy b: a:
```

若要使用软盘驱动器 A 将软盘复制到另一张软盘，请先切换到 C 驱动器，然后键入：

```
diskcopy a: a:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [xcopy 命令](xcopy.md)

- [复制命令](copy.md)
