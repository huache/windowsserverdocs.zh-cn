---
title: ReFSUtil
description: ReFSUtil 是 Windows 和 Windows Server 中包含的一种工具，它尝试诊断严重损坏的 ReFS 卷、标识剩余文件并将这些文件复制到另一个卷。
author: laknight5
ms.author: laknight
ms.date: 6/29/2020
ms.prod: windows-server
ms.technology: storage-file-systems
ms.topic: article
ms.openlocfilehash: 0d7c1bf79695c2ddd03943744ebf1df4827d365c
ms.sourcegitcommit: 457e88e5aa6be13a2bffdb8e434a8efc3698678f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "85549142"
---
# <a name="refsutil"></a>ReFSUtil

>适用于：Windows Server 2019、Windows 10

ReFSUtil 是 Windows 和 Windows Server 中包含的一种工具，它尝试诊断严重损坏的 ReFS 卷、标识剩余文件并将这些文件复制到另一个卷。 这在 Windows 10 的%SystemRoot%\Windows\System32 文件夹中或 Windows Server 的% SystemRoot% \\ System32 文件夹中。

ReFS 抢救目前是 ReFSUtil 的主要功能，适用于从在 "磁盘管理" 中显示为 "原始" 的卷中恢复数据。 ReFS 抢救分为两个阶段：扫描阶段和复制阶段。 在自动模式下，扫描阶段和复制阶段将按顺序运行。 在手动模式下，每个阶段都可以单独运行。 进度和日志保存在工作目录中，以允许单独运行阶段，以及暂停和恢复扫描阶段。 如果卷为 RAW 卷，则不应使用 ReFSutil。 如果是只读的，则数据仍可访问。

## <a name="automatic-mode-command-line-usage"></a>自动模式命令行使用

### <a name="quick-automatic-mode-command-line-usage"></a>快速自动模式命令行使用

```dos
refsutil salvage -QA <source volume> <working directory> <target directory> <options>
```
它将执行快速扫描阶段，然后执行复制阶段。 此模式的运行速度更快，因为它假定卷的某些关键结构没有损坏，因此不需要扫描整个卷来查找它们。 这还可以减少过时文件/目录/卷的恢复。

### <a name="full-automatic-mode-command-line-usage"></a>完全自动模式命令行使用

```dos
refsutil salvage -FA <source volume> <working directory> <target directory> <options>
```

它将执行完全扫描阶段，后跟复制阶段。 此模式可能需要较长时间，因为它会扫描整个卷中是否有任何可恢复文件/目录/卷。

## <a name="manual-mode-command-line-usage"></a>手动模式命令行用法

### <a name="diagnose-phase-command-line-usage"></a>诊断阶段命令行用法

```dos
refsutil salvage -D <source volume> <working directory> <options>
```

首先，请尝试确定 \<source volume\> 是否是 ReFS 卷，并确定该卷是否可装入。 当卷不可装入时，将确定原因。 这是一个独立的阶段。

### <a name="quick-scan-phase-command-line-usage"></a>快速扫描阶段命令行用法

```dos
refsutil salvage -QS <source volume> <working directory> <options>
```

快速扫描 \<source volume\> 任何可恢复文件。 此模式的运行速度更快，因为它假定卷的某些关键结构没有损坏，因此不需要扫描整个卷来查找它们。 这还可以减少过时文件/目录/卷的恢复。 发现的文件将记录到 "foundfiles" \<volume signature\> 。txt " \<working directory\> 。 如果扫描阶段之前已停止，则再次运行带有-QS 标志的将从中断的位置继续扫描。

### <a name="full-scan-phase-command-line-usage"></a>完全扫描阶段命令行用法

```dos
refsutil salvage -FS <source volume> <working directory> <options>
```

整个扫描 \<source volume\> 所有可恢复的文件。 此模式可能需要较长时间，因为它会扫描整个卷中是否有任何可恢复文件。
发现的文件将记录到 "foundfiles" \<volume signature\> 。txt " \<working directory\> 。 如果扫描阶段之前已停止，则再次运行带有-FS 标志的将从中断的位置继续扫描。

### <a name="copy-phase-command-line-usage"></a>复制阶段命令行用法

```dos
refsutil salvage -C <source volume> <working directory> <target directory>
<options>
```

复制 "foundfiles" 中所 \<volume signature\> 述的所有文件。txt "到 \<target
directory\> 。 如果扫描阶段停止太早，"foundfiles \<volume
signature\> "。txt "可能尚未编写，因此不会将任何文件复制到 \<target directory\> 。

### <a name="copy-phase-with-list-command-line-usage"></a>使用 list 命令行使用的复制阶段

```dos
refsutil salvage -SL <source volume> <working directory> <target
directory> <file list> <options>
```

将中的所有文件 \<file list\> 复制 \<source volume\> 到 \<target
directory\> 。 在中，文件 \<file list\> 必须首先由扫描阶段标识，但扫描需要尚未运行完成。 \<file list\>可以通过将 "foundfiles" \<volume signature\>txt "移到新文件中，删除引用不应还原的文件的行，并保留应还原的文件。 在筛选 "foundfiles" 时，PowerShell cmdlet 选择字符串可能会很有 \<volume signature\> 帮助。txt "，只包含所需的路径、扩展名或文件名。

### <a name="copy-phase-with-interactive-console"></a>带有交互式控制台的复制阶段

```dos
refsutil salvage -IC <source volume> <working directory> <options>
```

为高级用户在交互控制台中抢救文件。 此模式还需要从任一扫描阶段生成的文件。

## <a name="parameters"></a>参数

| 参数             | 说明                                                                     |
| --------------------- | --------------------------------------------------------------------------------------- |
| \<source volume\>     | 要处理的 ReFS 卷。 驱动器号的格式为 "L：" 或卷装入点的路径。           |
| \<working directory\> | 用于存储临时信息和日志的位置。 **不得位于**上 \<source volume\> 。  |
| \<target directory\>  | 标识的文件将复制到的位置。 **不得位于**上 \<source volume\> 。 |
| \-m         | 恢复所有可能的文件，包括删除的文件。 对于 refsutil 抢救 v1，此选项将被忽略。 警告：此操作可能需要较长时间才能运行，这可能会导致意外的结果。 |
| \-向量         | 详细模式                                                                                           |
| \-x-blade         | 必要时，请首先强制卸除卷。 卷的所有打开的句柄将无效。 例如： refsutil 抢救-QA R： N： \\ 工作 N： \\ DATA x                                  |
