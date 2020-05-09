---
title: diskpart
description: Diskpart 命令解释器的参考主题，可帮助你管理计算机驱动器。
ms.prod: windows-server
ms.technology: storage
author: jasongerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 8b6d36e428daaefd7cf26e42170442373fc7551c
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992574"
---
# <a name="diskpart"></a>diskpart

> 适用于： Windows 10，Windows 8.1，Windows 8，Windows 7，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012 和 Windows Server 2008 R2，Windows Server 2008

Diskpart 命令解释器可帮助你管理计算机的驱动器（磁盘、分区、卷或虚拟硬盘）。

你必须首先列出，然后选择一个对象来使其成为焦点，然后才能使用**diskpart**命令。 对象具有焦点后，你键入的任何 diskpart 命令都将作用于该对象。

## <a name="list-available-objects"></a>列出可用对象

可以使用以下方法列出可用对象，并确定对象的编号或驱动器号：

- `list disk`-显示计算机上的所有磁盘。

- `list volume`-显示计算机上的所有卷。

- `list partition`-显示在计算机上有焦点的磁盘上的分区。

- `list vdisk`-显示计算机上的所有虚拟磁盘。

运行**列表**命令后，会在具有焦点的对象旁边显示星号（*）。

## <a name="determine-focus"></a>确定焦点

选择对象时，焦点一直停留在该对象上，直至选择其他对象。 例如，如果焦点设置在磁盘0上，并且选择了磁盘2上的卷8，则焦点将从磁盘0转移到磁盘2、卷8。

某些命令会自动更改焦点。 例如，在创建新的分区时，焦点会自动切换到新的分区。

只能将焦点放到所选磁盘上的分区。 分区有焦点后，相关卷（如果有）也具有焦点。 如果卷具有焦点，则相关磁盘和分区也会获得焦点，前提是该卷映射到单个特定分区。 如果不是这样，则对磁盘和分区的关注会丢失。

## <a name="syntax"></a>语法

若要启动 diskpart 命令解释器，请在命令提示符下键入：

```
diskpart <parameter>
```

> [!IMPORTANT]
> 你必须是本地**管理员**组或具有类似权限的组才能运行 diskpart。

### <a name="parameters"></a>参数

可以从 Diskpart 命令解释器运行以下命令：

| Command | 说明 |
| ------- | ----------- |
| [active](active.md) | 将具有焦点的磁盘分区标记为活动分区。 |
| [add](add.md) | 将选中的简单卷镜像到指定磁盘。 |
| [assign](assign.md) | 给选中的卷分配一个驱动器号或装入点。 |
| [附加 vdisk](attach-vdisk.md) | 附加（有时称为装载或曲面）虚拟硬盘（VHD），以使其作为本地硬盘驱动器出现在主计算机上。 |
| [attributes](attributes.md) | 显示、设置或清除磁盘或卷的属性。 |
| [automount](automount.md) | 启用或禁用自动装载功能。 |
| [break](break.md) | 将选中的镜像卷分为两个简单卷。 |
| [clean](clean.md) | 从选中的磁盘中删除所有分区或卷格式。 |
| [compact vdisk](compact-vdisk.md) | 减小动态扩展虚拟硬盘（VHD）文件的物理大小。 |
| [convert](convert.md) | 将文件分配表（FAT）和 FAT32 卷转换为 NTFS 文件系统，从而使现有文件和目录保持不变。 |
| [创建](create.md) | 在磁盘上创建分区，在一个或多个磁盘上创建卷，或在虚拟硬盘（VHD）上创建分区。 |
| [delete](delete.md) | 删除分区或卷。 |
| [分离 vdisk](detach-vdisk.md) | 将所选虚拟硬盘（VHD）从主计算机上的本地硬盘驱动器上停止显示。 |
| [仔细](detail.md) | 显示有关所选磁盘、分区、卷或虚拟硬盘（VHD）的信息。 |
| [exit](exit.md) | 退出 diskpart 命令解释器。 |
| [展开 vdisk](expand-vdisk.md) | 将虚拟硬盘（VHD）扩展到指定的大小。 |
| [扩展](extend.md) | 将具有焦点的卷或分区以及其文件系统扩展到磁盘上的可用（未分配）空间中。 |
| [文件系统](filesystems.md) | 显示具有焦点的卷的当前文件系统的相关信息，并列出格式化卷时支持的文件系统。 |
| [format](format.md) | 格式化磁盘以接受 Windows 文件。 |
| [gpt](gpt.md) | 将 gpt 属性分配给包含基本 GUID 分区表（gpt）磁盘的分区。 |
| [help](help.md) | 显示有关指定命令的可用命令或详细帮助信息的列表。 |
| [import](import.md) | 将外部磁盘组导入到本地计算机的磁盘组。 |
| [不用](inactive.md) | 在基本主启动记录（MBR）磁盘上将具有焦点的系统分区或启动分区标记为非活动状态。 |
| [list](list.md) | 显示磁盘中的分区、磁盘中的卷或虚拟硬盘（Vhd）的列表。 |
| [merge vdisk](merge-vdisk.md) | 将差异虚拟硬盘（VHD）与其对应的父 VHD 合并在一起。 |
| [断开](offline.md) | 使联机磁盘或卷进入脱机状态。 |
| [联机](online.md) | 使脱机磁盘或卷处于联机状态。 |
| [recover](recover.md) | 刷新磁盘组中所有磁盘的状态，尝试恢复无效磁盘组中的磁盘，并重新同步已过时的镜像卷和 RAID-5 卷。 |
| [rem](rem.md) | 提供一种向脚本添加注释的方法。 |
| [remove](remove.md) | 从卷中删除驱动器号或装入点。 |
| [修正](repair.md) | 通过将故障磁盘区域替换为指定的动态磁盘，修复具有焦点的 RAID-5 卷。 |
| [扫描](rescan.md) | 查找可能已添加到计算机的新磁盘。 |
| [变化](retain.md) | 准备要用作启动卷或系统卷的现有动态简单卷。 |
| [北京](san.md) | 显示或设置操作系统的存储区域网络（san）策略。 |
| [select](select.md) | 将焦点移到磁盘、分区、卷或虚拟硬盘（VHD）。 |
| [设置 id](set-id.md) | 更改具有焦点的分区的 "分区类型" 字段。 |
| [shrink](shrink.md) | 按指定的数量减小所选卷的大小。 |
| [uniqueid](uniqueid.md) | 显示或设置具有焦点的磁盘的 GUID 分区表（GPT）标识符或主启动记录（MBR）签名。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [磁盘管理概述](https://docs.microsoft.com/windows-server/storage/disk-management/overview-of-disk-management)

- [Windows PowerShell 中的存储 Cmdlet](https://docs.microsoft.com/powershell/module/storage/)
