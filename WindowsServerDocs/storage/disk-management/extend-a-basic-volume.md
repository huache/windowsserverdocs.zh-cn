---
title: 扩展基本卷
description: 可以向 Windows 中的现有卷添加空间，并将它扩展到驱动器上的空白空间中，但前提是空白空间里没有卷（未分配）并且紧接在要扩展的卷后，两者之间没有其他卷。 本文介绍如何执行此操作。
ms.date: 12/19/2019
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 19b48bd74dad4e20780b41852afbee15f5ec1ade
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966099"
---
# <a name="extend-a-basic-volume"></a>扩展基本卷

> **适用于：** Windows 10、Windows 8.1、Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

可以使用“磁盘管理”向现有卷添加空间，并将它扩展到驱动器上的空白空间中，但前提是空白空间里没有卷（未分配）并且紧接在要扩展的卷后，两者之间没有其他卷，如下图所示。 必须使用 NTFS 或 ReFS 文件系统对要扩展的卷进行格式化。

:::image type="content" source="media/extend-volume-space-highlighted.png" alt-text="“磁盘管理”，显示了卷可扩展到的可用空间。":::

## <a name="to-extend-a-volume-by-using-disk-management"></a>使用“磁盘管理”扩展卷

下面介绍了如何在卷位于驱动器上后立即将卷扩展到空白空间：

1. 使用管理员权限打开磁盘管理。

   一种简单的打开方式是在任务栏上的搜索框中键入“计算机管理”，选中并按住（或右键单击）“计算机管理”，然后选择“以管理员身份运行” > “是”     。 打开“计算机管理”后，转到“存储” > “磁盘管理”   。
2. 选中并按住（或右键单击）要扩展的卷，然后选择“扩展卷”  。

   如果“扩展卷”选项呈灰显状态，请检查下列内容  ：
    - “磁盘管理”或“计算机管理”是否是使用管理员权限打开的
    - 紧接卷之后的（卷的右侧）是否为未分配空间，如上图所示。 如果未分配空间与要扩展的卷之间有另一个卷，你可以删除中间的卷和此卷上的所有文件（请确保先备份或转移任何重要的文件！），使用可在不破坏数据的情况下移动卷的非 Microsoft 磁盘分区应用，或者跳过扩展卷这一步骤，改为在未分配空间中创建一个单独的卷。
    - 是否使用 NTFS 或 ReFS 文件系统对卷进行了格式化。 由于不能扩展其他文件系统，因此你需要移动或备份此卷上的文件，然后使用 NTFS 或 ReFS 文件系统对此卷进行格式化。
    - 如果磁盘大于 2 TB，请确保它使用的是 GPT 分区方案。 若要在磁盘上使用的空间超过了 2 TB，则必须使用 GPT 分区方案对磁盘进行初始化。 若要转换为 GPT，请参阅[将 MBR 磁盘更改为 GPT 磁盘](change-an-mbr-disk-into-a-gpt-disk.md)。
    - 如果仍无法扩展卷，请尝试搜索站点 [Microsoft 社区 - 文件、文件夹和存储](https://answers.microsoft.com/en-us/windows/forum/windows_10-files?sort=lastreplydate&dir=desc&tab=All&status=all&mod=&modAge=&advFil=&postedAfter=&postedBefore=&threadType=all&isFilterExpanded=true&tm=1514405359639)，并且如果没有找到答案，可以在那里发布问题，Microsoft 或其他社区成员将尝试提供帮助，或者[联系 Microsoft 支持部门](https://support.microsoft.com/contactus/)。

3. 选择“下一步”，然后在向导的“选择磁盘”页面上（此处显示的页面），指定要扩展的卷大小   。 通常情况下，你需要使用默认值，这会使用所有可用空间，但如果想在可用空间中创建额外的卷，则可以使用一个较小的值。

   :::image type="content" source="media/extend-volume-wizard.png" alt-text="“扩展卷向导”，显示了要扩展到占用所有可用空间的卷":::

4. 选择“下一步”，然后选择“完成”以扩展卷   。

## <a name="to-extend-a-volume-by-using-powershell"></a>使用 PowerShell 扩展卷

1. 选中并按住（或右键单击）“开始”按钮，然后选择“Windows PowerShell (管理员)”。
2. 输入以下命令将卷大小调整为最大大小，指定要在 $drive_letter 变量中扩展的卷的驱动器号  ：

   ```PowerShell
   # Variable specifying the drive you want to extend
   $drive_letter = "C"

   # Script to get the partition sizes and then resize the volume
   $size = (Get-PartitionSupportedSize -DriveLetter $drive_letter)
   Resize-Partition -DriveLetter $drive_letter -Size $size.SizeMax
   ```

## <a name="see-slso"></a>另请参阅

- [Resize-Partition](/powershell/module/storage/resize-partition)
- [Diskpart extend](../../administration/windows-commands/extend.md)
