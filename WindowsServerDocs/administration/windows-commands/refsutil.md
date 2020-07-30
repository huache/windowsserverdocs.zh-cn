---
title: ReFSUtil
description: 有关 ReFSUtil 工具的参考文章，该工具尝试诊断严重损坏的 ReFS 卷，确定剩余文件，并将这些文件复制到另一个卷。
author: laknight5
ms.author: laknight
ms.date: 6/29/2020
ms.prod: windows-server
ms.technology: windows-commands
ms.topic: article
ms.openlocfilehash: 3afc96970bb0350a3c1168c520cc20ad4f2254af
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409718"
---
# <a name="refsutil"></a>ReFSUtil

> 适用于：Windows Server 2019、Windows 10

ReFSUtil 是 Windows 和 Windows Server 中包含的一种工具，它尝试诊断严重损坏的 ReFS 卷、标识剩余文件并将这些文件复制到另一个卷。 此文件位于文件夹中的 Windows 10 `%SystemRoot%\Windows\System32` 或文件夹中的 Windows Server 中 `%SystemRoot%\System32` 。

ReFS 抢救是 ReFSUtil 的主要功能，适用于从在 "磁盘管理" 中显示为 "原始" 的卷中恢复数据。 ReFS 抢救分为两个阶段：扫描阶段和复制阶段。 在自动模式下，扫描阶段和复制阶段将按顺序运行。 在手动模式下，每个阶段都可以单独运行。 进度和日志保存在工作目录中，以允许单独运行阶段，以及暂停和恢复扫描阶段。 不需要使用 ReFSutil 工具，除非该卷为 RAW。 如果是只读的，则数据仍可访问。

## <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<source volume>` | 指定要处理的 ReFS 卷。 驱动器号的格式必须为 "L："，或者必须提供卷装入点的路径。 |
| `<working directory>` | 指定存储临时信息和日志的位置。 它不得**位于**上 `<source volume>` 。 |
| `<target directory>` | 指定将标识文件复制到的位置。 它不得**位于**上 `<source volume>` 。 |
| \-m | 恢复所有可能的文件，包括删除的文件。<p>**警告：** 此参数不仅会导致进程运行较长时间，还会导致意外的结果。 |
| \-向量 | 指定使用详细模式。 |
| \-x | 必要时强制首先卸除卷。 卷的所有打开的句柄均无效。 例如，`refsutil salvage -QA R: N:\WORKING N:\DATA -x`。 |

## <a name="usage-and-available-options"></a>使用情况和可用选项

### <a name="quick-automatic-mode-command-line-usage"></a>快速自动模式命令行使用

执行快速扫描阶段，后跟复制阶段。 此模式的运行速度更快，因为它假定卷的某些关键结构没有损坏，因此不需要扫描整个卷来查找它们。 这还可以减少过时文件/目录/卷的恢复。

```
refsutil salvage -QA <source volume> <working directory> <target directory> <options>
```

### <a name="full-automatic-mode-command-line-usage"></a>完全自动模式命令行使用

执行完全扫描阶段，后跟复制阶段。 此模式可能需要较长时间，因为它会扫描整个卷中是否有任何可恢复文件/目录/卷。

```
refsutil salvage -FA <source volume> <working directory> <target directory> <options>
```

### <a name="diagnose-phase-command-line-usage-manual-mode"></a>诊断阶段命令行使用情况（手动模式）

首先，请尝试确定 `<source volume>` 是否是 ReFS 卷并确定该卷是否可装入。 如果卷不可装入，将提供原因。 这是一个独立的阶段。

```
refsutil salvage -D <source volume> <working directory> <options>
```

### <a name="quick-scan-phase-command-line-usage"></a>快速扫描阶段命令行用法

`<source volume>`对任何可恢复文件执行的快速扫描。 此模式的运行速度更快，因为它假定卷的某些关键结构没有损坏，因此不需要扫描整个卷来查找它们。 这还可以减少过时文件/目录/卷的恢复。 发现的文件被记录到 `foundfiles.<volume signature>.txt` 文件中，该文件位于中 `<working directory>` 。 如果扫描阶段之前已停止，则以 **-QS**标志运行将再次从其停止的位置恢复扫描。

```
refsutil salvage -QS <source volume> <working directory> <options>
```

### <a name="full-scan-phase-command-line-usage"></a>完全扫描阶段命令行用法

扫描整个 `<source volume>` ，查找任何可恢复的文件。 此模式可能需要较长时间，因为它会扫描整个卷中是否有任何可恢复文件。 发现的文件将记录到 `foundfiles.<volume signature>.txt` 文件中，该文件位于中 `<working directory>` 。 如果扫描阶段之前已停止，则以 **-FS**标志再次运行将从其停止的位置恢复扫描。

```
refsutil salvage -FS <source volume> <working directory> <options>
```

### <a name="copy-phase-command-line-usage"></a>复制阶段命令行用法

将文件中描述的所有文件复制 `foundfiles.<volume signature>.txt` 到 `<target directory>` 。 如果停止扫描阶段的过程过早，可能是因为该 `foundfiles.<volume signature>.txt` 文件不存在，因此不会将文件复制到 `<target directory>` 。

```
refsutil salvage -C <source volume> <working directory> <target directory> <options>
```

### <a name="copy-phase-with-list-command-line-usage"></a>使用 list 命令行使用的复制阶段

将中的所有文件复制 `<file list>` `<source volume>` 到 `<target directory>` 。 中的文件 `<file list>` 必须首先由扫描阶段标识，不过，扫描不需要运行到完成。 `<file list>`可以通过复制 `foundfiles.<volume signature>.txt` 到新文件、删除引用不应还原的文件的行以及保留应还原的文件来生成。 PowerShell cmdlet**选择字符串**可能有助于筛选 `foundfiles.<volume signature>.txt` 以仅包含所需的路径、扩展名或文件名。

```
refsutil salvage -SL <source volume> <working directory> <target directory> <file list> <options>
```

### <a name="copy-phase-with-interactive-console"></a>带有交互式控制台的复制阶段

高级用户可以使用交互式控制台来抢救文件。 此模式还需要从任一扫描阶段生成的文件。

```
refsutil salvage -IC <source volume> <working directory> <options>
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
