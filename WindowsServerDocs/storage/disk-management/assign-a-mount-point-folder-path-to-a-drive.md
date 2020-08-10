---
title: 为驱动器分配装入点文件夹路径。
description: 本文介绍如何为驱动器分配装入点文件夹路径（而不是驱动器号）。
ms.date: 06/07/2020
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 447eff6e9168825cec01d481ec9cb7e25431ac3e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87936089"
---
# <a name="mount-a-drive-in-a-folder"></a>在文件夹中装载驱动器

> **适用于：** Windows 10、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

如果需要，可以使用“磁盘管理”在文件夹（而不是驱动器号）中装载（使驱动器可访问）。 这样可使驱动器显示为一个文件夹。 只能在基本或动态 NTFS 卷的空文件夹中装载驱动器。

## <a name="mounting-a-drive-in-an-empty-folder"></a>将驱动器装载到空文件夹中

> [!NOTE]
> 至少必须是“备份操作员”或“管理员”组的成员才能完成这些步骤。

### <a name="to-mount-a-drive-in-an-empty-folder-by-using-the-windows-interface"></a>使用 Windows 界面将驱动器装载到空文件夹中

1.  在“磁盘管理器”中，右键单击包含要在其中装载驱动器的文件夹的分区或卷。
2. 依次单击“更改驱动器号和路径”、“添加” 。
3. 单击“装入以下空白 NTFS 文件夹中”。
4. 键入 NTFS 卷上空文件夹的路径，或者单击“浏览”以找到它。

### <a name="to-mount-a-drive-in-an-empty-folder-using-a-command-line"></a>使用命令行在空文件夹中装载驱动器

1.  打开命令提示符并键入 `diskpart`。

2.  在 **DISKPART** 提示符下，键入 `list volume`，并记下要为其分配路径的卷编号。

3.  在 **DISKPART** 提示符下，键入 `select volume <volumenumber>`，指定要分配其路径的卷编号。

5.  在 DISKPART 提示符下，键入 `assign [mount=<path>]`。

### <a name="to-remove-a-mount-point"></a>删除装载点

若要删除装载点，以禁止通过文件夹访问该驱动器：

1. 选择并按住（或右键单击）装载到文件夹的驱动器，然后选择“更改驱动器号和路径”。
2. 从列表中选择该文件夹，然后选择“删除”。

| 值 | 说明 |
| --- | --- |
| **list volume** | 显示所有磁盘上的基本卷和动态卷的列表。 |
| **select volume**        | 选择指定的卷（其中 <em>volumenumber</em> 是卷编号），并赋予其焦点。 如果未指定卷，则 **select** 命令会列出具有焦点的当前卷。 可以通过编号、驱动器号或装入点文件夹路径来指定卷。 在基本磁盘上，如果选择卷，则还会赋予相应的分区焦点。|
| **assign** | <ul><li> 将驱动器号或装入点文件夹路径分配给具有焦点的卷。 如果未指定驱动器号或装入点文件夹路径，则将分配下一个可用的驱动器号。 如果驱动器号或装入点文件夹路径已被占用，则会出错。</li>  <li>使用 **assign** 命令可以更改与可移动驱动器相关联的驱动器号。</li> <li> 无法将驱动器号分配给引导卷或包含分页文件的卷。 此外，不能将驱动器号分配给原始设备制造商 (OEM) 分区、EFI 系统分区或基本数据分区以外的其他任何 GPT 分区。</li></ul> |
| **mount=** <em>path</em> | 指定安装的驱动器所位于的现有空 NTFS 文件夹。  |

## <a name="additional-considerations"></a>其他注意事项

-   如果管理的是本地或远程计算机，则可以浏览该计算机上的 NTFS 文件夹。
-   装入点文件夹路径仅适用于基本或动态 NTFS 卷上的空文件夹。
-   若要修改装入点文件夹路径，请删除它，然后使用新位置创建新文件夹路径。 无法直接修改装入点文件夹路径。
-   为驱动器分配装入点文件夹路径时，请使用“事件查看器”检查系统日志中指明装入点文件夹路径故障的任何群集服务错误或警告。 这些错误会在“源”列中列为“ClusSvc”，在“类别”列中列为“物理磁盘资源”。
-   还可以使用 [mountvol](https://go.microsoft.com/fwlink/?linkid=64111) 命令创建已装载的驱动器。

## <a name="additional-references"></a>其他参考
-   [命令行语法表示法](/previous-versions/orphan-topics/ws.11/cc742449(v=ws.11))
