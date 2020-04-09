---
title: DiskPart
description: 适用于 DiskPart 的 Windows 命令主题，可帮助你管理计算机驱动器。
ms.prod: windows-server
ms.technology: storage
author: jasongerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 45fe66e4843b96db8e4593c0e963e4a80dbd22c2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845470"
---
# <a name="diskpart"></a>DiskPart

>适用于： Windows 10，Windows 8.1，Windows 8，Windows 7，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012 和 Windows Server 2008 R2，Windows Server 2008

DiskPart 命令可帮助你管理计算机的驱动器（磁盘、分区、卷或虚拟硬盘）。 

你必须首先列出，然后选择一个对象来使其成为焦点，然后才能使用 DiskPart 命令。 当对象具有焦点时，键入的任何 DiskPart 命令都将作用于该对象。

## <a name="list-the-available-objects"></a>列出可用对象

可以使用以下方法列出可用对象，并确定对象的编号或驱动器号：

- `list disk`-显示计算机上的所有磁盘。

- `list volume`-显示计算机上的所有卷。

- `list partition`-显示在计算机上有焦点的磁盘上的分区。

- `list vdisk`-显示计算机上的所有虚拟磁盘。

使用**list**命令时，会在具有焦点的对象旁边显示一个星号（\*）。

## <a name="determine-focus"></a>确定焦点

选择对象时，焦点一直停留在该对象上，直至选择其他对象。 例如，如果焦点设置在磁盘0上，并且选择了磁盘2上的卷8，则焦点将从磁盘0转移到磁盘2、卷8。

某些命令会自动更改焦点。 例如，在创建新的分区时，焦点会自动切换到新的分区。

只能将焦点放到所选磁盘上的分区。 选中某个分区时，也会选中相关的卷（如果有）。 选中某个卷时，如果该卷映射到单个特定分区，则也会选中相关的磁盘和分区。 如果不是这样，则对磁盘和分区的关注会丢失。

## <a name="diskpart-commands"></a>DiskPart 命令

若要启动 DiskPart 命令解释器，请在命令提示符下键入：

```
diskpart
```

> [!IMPORTANT]
> 你必须是本地**管理员**组或具有类似权限的组才能运行 DiskPart。 

可以在 Diskpart 命令解释器中运行以下命令：

| Command | 说明 |
| ------- | ----------- |
| [Active](active.md) | 将具有焦点的磁盘分区标记为活动分区。 |
| [Add](add.md) | 将选中的简单卷镜像到指定磁盘。 |
| [将](assign.md) | 给选中的卷分配一个驱动器号或装入点。 |
| [附加 vdisk](attach-vdisk.md) | 附加（有时称为装载或曲面）虚拟硬盘（VHD），以使其作为本地硬盘驱动器出现在主计算机上。 |
| [属性](attributes.md) | 显示、设置或清除磁盘或卷的属性。 |
| [装载](automount.md) | 启用或禁用自动装载功能。 | 
| [分](break.md) | 将选中的镜像卷分为两个简单卷。 |
| [整洁](clean.md) | 从选中的磁盘中删除所有分区或卷格式。 |
| [Compact vdisk](compact-vdisk.md) | 减小动态扩展虚拟硬盘（VHD）文件的物理大小。 |
| [转换](convert.md) | 将文件分配表（FAT）和 FAT32 卷转换为 NTFS 文件系统，从而使现有文件和目录保持不变。 |
| [创建](create.md) | 在磁盘上创建分区，在一个或多个磁盘上创建卷，或在虚拟硬盘（VHD）上创建分区。 |
| [删除](delete.md) | 删除分区或卷。 |
| [分离 vdisk](detach-vdisk.md) | 将所选虚拟硬盘（VHD）从主计算机上的本地硬盘驱动器上停止显示。 |
| [仔细](detail.md) | 显示有关所选磁盘、分区、卷或虚拟硬盘（VHD）的信息。 |
| [退出](exit.md) | 退出 DiskPart 命令解释程序。 |
| [展开 vdisk](expand-vdisk.md) | 
| [Extend](extend.md) | 
| [文件系统](filesystems.md) | 
| [Format](format.md) | 
| [GPT](gpt.md) | 
| [帮助](help.md) | 
| [导入](import.md) | 
| [不用](inactive.md) | 
| [成员列表](list.md) | 
| [Merge vdisk](merge-vdisk.md) | 
| [断开](offline.md) | 
| [联机](online.md) | 
| [恢复](recover.md) | 
| [剩余](rem.md) | 
| [删除](remove.md) | 
| [修正](repair.md) | 
| [扫描](rescan.md) | 
| [变化](retain.md) | 
| [北京](san.md) | 
| [单击](select.md) | 
| [设置 id](set-id.md) | 
| [收缩](shrink.md) | 
| [Uniqueid](uniqueid.md) | 

## <a name="additional-references"></a>其他参考

- [命令行语法键]（command-line-syntax-key.md

- [磁盘管理概述](https://docs.microsoft.com/windows-server/storage/disk-management/overview-of-disk-management)

- [Windows PowerShell 中的存储 Cmdlet](https://docs.microsoft.com/powershell/module/storage/)
