---
title: 将动态磁盘更改回基本磁盘
description: 介绍如何将动态磁盘转换回基本磁盘。
ms.date: 12/18/2019
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: f866127bc43df307ac1a6a1fa44daac91ada5dcd
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966079"
---
# <a name="change-a-dynamic-disk-back-to-a-basic-disk"></a>将动态磁盘更改回基本磁盘

> **适用于：** Windows 10、Windows 8.1、Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题介绍如何删除动态磁盘上的所有内容，然后将其转换回基本磁盘。 已在 Windows 中弃用动态磁盘，不建议再使用它们。 相反，如果你希望将磁盘汇聚成更大的卷，建议使用基本磁盘或较新的[存储空间](https://support.microsoft.com/help/12438/windows-10-storage-spaces)技术。 如果要镜像 Windows 的引导卷，则可能需要使用硬件 RAID 控制器，例如许多主板上包含的 RAID 控制器。

> [!WARNING]
> 若要将动态磁盘转换回基本磁盘，必须删除磁盘中的所有卷，并永久擦除磁盘上的所有数据。 请确保备份所有要保留的数据，然后再继续操作。

## <a name="to-change-a-dynamic-disk-back-to-a-basic-disk-by-using-disk-management"></a>通过使用“磁盘管理”将动态磁盘更改回基本磁盘

1.  备份要从动态磁盘转换为基本磁盘的磁盘上的所有卷。

2. 使用管理员权限打开磁盘管理。

   一种简单的打开方式是在任务栏上的搜索框中键入“计算机管理”，选中并按住（或右键单击）“计算机管理”，然后选择“以管理员身份运行” > “是”   。 打开“计算机管理”后，转到“存储” > “磁盘管理” 。

2.  在“磁盘管理”中，选中并按住（或右键单击）要转换为基本磁盘的动态磁盘上的每个卷，然后单击“删除卷”。

3.  删除了磁盘上的所有卷后，右键单击该磁盘，然后单击“转换成基本磁盘”。

## <a name="to-change-a-dynamic-disk-back-to-a-basic-disk-by-using-a-command-line"></a>通过使用命令行将动态磁盘更改回基本磁盘

1.  备份要从动态磁盘转换为基本磁盘的磁盘上的所有卷。

2.  打开命令提示符并键入 `diskpart`。

3.  在 DISKPART 提示符下，键入 `list disk`。 请记下要转换为基本磁盘的磁盘编号。

4.  在 DISKPART 提示符下，键入 `select disk <disknumber>`。

5.  在 DISKPART 提示符下，键入 `detail disk`。

6.  对于磁盘上的每个卷，在“DISKPART”提示符下，键入 `select volume= <volumenumber>`，然后键入 `delete volume`。

7.  在“DISKPART”提示符下，键入 `select disk <disknumber>`，并指定你希望转换为基本磁盘的磁盘编号。

8.  在 DISKPART 提示符下，键入 `convert basic`。

| 值  | 说明 |
| --- | --- |
| **list disk**                         | 显示磁盘列表和有关磁盘的信息，例如磁盘大小、可用空间量、磁盘是基本磁盘还是动态磁盘，以及磁盘是使用主启动记录 (MBR) 还是 GUID 分区表 (GPT) 分区样式。 用星号 (*) 标记的磁盘具有焦点。 |
| **select disk** <em>disknumber</em>   | 选择指定的磁盘（其中 <em>disknumber</em> 是磁盘编号），并赋予其焦点。  |
| **detail disk** <em>disknumber</em>   | 显示所选磁盘的属性和该磁盘上的卷。  |
| **select volume** <em>disknumber</em> | 选择指定的卷（其中 <em>disknumber</em> 是卷编号），并赋予其焦点。 如果未指定卷，则 select 命令会列出具有焦点的当前卷。 可以通过编号、驱动器号或装入点路径指定卷。 在基本磁盘上，如果选择卷，则还会赋予相应的分区焦点。 |
| delete volume                     | 删除所选的卷。 无法删除系统卷、引导卷或任何包含活动页面文件或故障转储（内存转储）的卷。 |
| convert basic | 将空动态磁盘转换为基本磁盘。  |

## <a name="additional-considerations"></a>其他注意事项

-   将磁盘更改回基本磁盘之前，磁盘不得包含任何卷或数据。 如果你想要保留数据，请先将数据备份或移动到另一个卷上，然后再将磁盘转换为基本磁盘。
-   将动态磁盘更改回基本磁盘之后，你在该磁盘上只能创建分区和逻辑驱动器。

## <a name="additional-references"></a>其他参考

-   [命令行语法表示法](/previous-versions/orphan-topics/ws.11/cc742449(v=ws.11))
