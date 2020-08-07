---
title: defrag
description: 用于在本地卷上查找并合并零碎文件以提高系统性能的 defrag 命令的参考文章。
ms.topic: article
ms.assetid: aaf1d1ac-996a-4282-9b4d-1e8245ff162c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c68edbb4511df12912adbc666201d5a381c06fe3
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891485"
---
# <a name="defrag"></a>defrag

> 适用于： Windows 10，Windows Server (半年通道) ，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

查找并合并本地卷上的零碎文件以提高系统性能。

本地**Administrators**组中的成员身份或等效身份是运行此命令所需的最低要求。

## <a name="syntax"></a>语法

```
defrag <volumes> | /c | /e <volumes>    [/h] [/m [n]| [/u] [v]]
defrag <volumes> | /c | /e <volumes> /a [/h] [/m [n]| [/u] [v]]
defrag <volumes> | /c | /e <volumes> /x [/h] [/m [n]| [/u] [v]]
defrag <volume> [<parameters>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<volume>` | 指定要进行碎片整理或分析的卷的驱动器号或装入点路径。 |
| /a | 在指定的卷上执行分析。 |
| /c | 对所有卷执行此操作。 |
| /d | 执行传统的碎片整理 (这是默认) 。 但在分层卷上，传统碎片整理仅在容量层上执行。 |
| /e | 在除指定的卷之外的所有卷上执行该操作。 |
| /g | 优化指定卷上的存储层。 |
| /h | 以普通优先级运行操作 (默认为低) 。 |
| /i [n] | 每个卷上最多可运行 n 个层优化。 |
| 遇到 | 在指定的卷上执行碎片合并。 |
| /l | 对指定的卷执行重新剪裁。 |
| /m [n] | 在后台并行运行每个卷上的操作。 最多 n 个线程并行优化存储层。 |
| /o | 为每种媒体类型执行适当的优化。 |
| /t  | 跟踪指定卷上已在进行的操作。 |
| /U | 在屏幕上打印操作进度。 |
| /v | 打印包含碎片统计信息的详细输出。 |
| /x | 在指定卷上执行可用空间合并。 |
| /? | 显示此帮助信息。 |

#### <a name="remarks"></a>备注

- 不能对特定文件系统卷或驱动器进行碎片整理，包括：

  - 文件系统锁定的卷。

  - 文件系统标记为脏的卷，指出可能的损坏。<br>必须先运行， `chkdsk` 然后才能对此卷或驱动器进行碎片整理。 你可以使用命令确定卷是否已更新 `fsutil dirty` 。

  - 网络驱动器。

  - CD-ROM。

  - 文件系统卷不是**NTFS**、 **ReFS**、 **Fat**或**Fat32**。

- 你无法计划对固态驱动器 (SSD) 或驻留在 SSD 上的虚拟硬盘 (VHD) 上的卷进行碎片整理。

- 若要执行该过程，你必须是本地计算机上 Administrators 组的成员，或你必须已被委派适当的权限。 如果计算机已加入域，则 Domain Admins 组的成员也许能够执行该过程。 作为最佳安全方案，请考虑使用**运行方式**来执行此过程。

- 卷必须至少具有15% 的可用空间，**碎片整理**才能完整地对其进行碎片整理。 **defrag**使用此空间作为文件片段的排序区域。 如果卷的可用空间小于15%，则**defrag**只对其进行部分碎片整理。 若要增加卷上的可用空间，请删除不需要的文件或将其移到另一个磁盘上。

- 当**碎片整理**正在分析卷并对其进行碎片整理时，它会显示闪烁的光标。 当**defrag**完成分析并对卷进行碎片整理时，它会显示分析报告、碎片整理报告或两个报告，然后退出到命令提示符。

- 默认情况下，如果未指定 **/a**或 **/v**参数，则**defrag**将显示分析和碎片整理报告的摘要。

- 您可以通过键入 "FileName.txt" 将报告发送到文本文件 **>** <em> </em>，其中*FileName.txt*为指定的文件名。 例如： `defrag volume /v > FileName.txt`

- 若要中断碎片整理进程，请在命令行上按**CTRL + C**。

- 运行**defrag**命令和磁盘碎片整理程序是相互排斥的。 如果使用磁盘碎片整理程序对卷进行碎片整理，并在命令行中运行**defrag**命令，则**defrag**命令将失败。 相反，如果运行**defrag**命令并打开磁盘碎片整理程序，磁盘碎片整理程序中的碎片整理选项将不可用。

## <a name="examples"></a>示例

若要在提供进度和详细输出时对驱动器 C 上的卷进行碎片整理，请键入：

```
defrag c: /u /v
```

若要在后台并行对驱动器 C 和 D 中的卷进行碎片整理，请键入：

```
defrag c: d: /m
```

若要对驱动器 C 上装载的卷执行碎片分析并提供进度，请键入：

```
defrag c: mountpoint /a /u
```

若要对具有普通优先级的所有卷进行碎片整理并提供详细的输出，请键入：

```
defrag /c /h /v
```

## <a name="scheduled-task"></a>计划任务

碎片整理进程将计划任务作为维护任务运行，这通常每周运行一次。 作为管理员，你可以使用 "**优化驱动器**" 应用来更改运行任务的频率。

- 从计划任务运行时， **defrag**会将以下策略准则用于 ssd：

  - **传统优化过程**。 包括**传统碎片整理**，例如移动文件以使它们合理连续和**重新剪裁**。 每月执行一次。 但是，如果忽略**传统碎片整理**和**重新剪裁**，则不会运行**分析**。

  - 如果在 SSD 上手动运行**传统碎片整理**，则在正常计划运行期间，下一个计划任务运行将执行**分析**和**重新剪裁**，但会跳过该 SSD 上的**传统碎片整理**。

  - 如果跳过**分析**，则不会在 "**优化驱动器**" 应用中看到更新的**上次运行**时间。 因此，**上次运行**时间最多可以有一个月的时间。

  - 你可能会发现计划的任务尚未对所有卷进行碎片整理。 这通常是因为：

    - 进程不会唤醒要运行的计算机。

    - 计算机未接通电源。 如果计算机正在使用电池电源运行，则不会运行该进程。

    - 计算机启动备份 (从空闲) 恢复。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [chkdsk](chkdsk.md)

- [fsutil](fsutil.md)

- [fsutil dirty](fsutil-dirty.md)

- [优化-批量 Powershell](/powershell/module/storage/optimize-volume?view=win10-ps)
