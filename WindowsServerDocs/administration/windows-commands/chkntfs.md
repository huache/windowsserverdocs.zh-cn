---
title: chkntfs
description: Chkntfs 命令的参考主题，它在计算机启动时显示或修改自动磁盘检查。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 93eca810-8699-4716-8e9d-aecd54f704be
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 69b8e21a7b43538b6296666d813f2b33daa8045f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82713661"
---
# <a name="chkntfs"></a>chkntfs

在计算机启动时显示或修改自动磁盘检查。 如果使用时没有选项， **chkntfs**将显示指定卷的文件系统。 如果计划运行自动文件检查，则**chkntfs**会显示指定的卷是否已更新，或是否计划在下次启动计算机时进行检查。

> [!NOTE]
> 若要运行**chkntfs**，你必须是 Administrators 组的成员。

## <a name="syntax"></a>语法

```
chkntfs <volume> [...]
chkntfs [/d]
chkntfs [/t[:<time>]]
chkntfs [/x <volume> [...]]
chkntfs [/c <volume> [...]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<volume>` [...] | 指定在计算机启动时要检查的一个或多个卷。 有效的卷包括驱动器号（后跟冒号）、装入点或卷名。 |
| /d | 还原所有**chkntfs**默认设置，但自动文件检查的倒计时时间除外。 默认情况下，当计算机启动时，所有卷都处于选中状态，并且**chkdsk**在那些更新的计算机上运行。 |
| /t [`:<time>`] | 将 Autochk 初始倒计时时间更改为指定的时间量（以秒为单位）。 如果未输入时间，则 **/t**将显示当前倒计时时间。 |
| /x `<volume>` [...] | 指定在计算机启动时要排除的一个或多个卷，即使卷被标记为需要**chkdsk**。 |
| /c `<volume>` [...] | 在计算机启动时计划要检查的一个或多个卷，并在那些已更新的卷上运行**chkdsk** 。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要显示驱动器 C 的文件系统类型，请键入：

```
chkntfs c:
```

> [!NOTE]
> 如果计划运行自动文件检查，则将显示其他输出，以指示驱动器是否处于脏状态，或是否已手动计划在下次启动计算机时进行检查。

若要显示 Autochk 初始倒计时时间，请键入：

```
chkntfs /t
```

若要将 Autochk 初始倒计时时间更改为30秒，请键入：

```
chkntfs /t:30
```

> [!NOTE]
> 虽然您可以将 Autochk 初始倒计时时间设置为零，但这样做将阻止您取消可能需要花费大量时间的自动文件检查。

若要排除多个卷的选中状态，必须在单个命令中列出每个卷。 例如，若要排除 D 和 E 卷，请键入：

```
chkntfs /x d: e:
```

> [!IMPORTANT]
> **/X**命令行选项不可累积总计。 如果多次键入，最新的条目将覆盖以前的条目。

若要计划对 D 卷（但不是 C 或 E 卷）进行自动文件检查，请按顺序键入以下命令：

```
chkntfs /d
chkntfs /x c: d: e:
chkntfs /c d:
```

> [!IMPORTANT]
> **/C**命令行选项为累积总计。 如果多次键入 **/c** ，则每个条目都将保留。 若要确保只检查特定的卷，请重置默认值以清除所有以前的命令，排除所有卷的检查，然后在所需的卷上计划自动文件检查。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
