---
title: 避免在生产环境中运行服务器工作负荷的虚拟机上使用检查点
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 1be75890-d316-495a-b9b7-be75fc1aac10
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: dadff29461786a454dc8d7ee6b46f3b567ef6bd8
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87994996"
---
# <a name="avoid-using-checkpoints-on-a-virtual-machine-that-runs-a-server-workload-in-a-production-environment"></a>避免在生产环境中运行服务器工作负荷的虚拟机上使用检查点

>适用于：Windows Server 2016



有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|操作|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

> [!NOTE]
> 在 Windows Server 2012 R2 中，虚拟机快照已重命名为 Hyper-v 管理器中的虚拟机检查点，以匹配 System Center 虚拟机管理中使用的术语。 有关详细信息，请参阅[检查点和快照概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn818483(v=ws.11))。

## <a name="issue"></a>问题

*找到了具有一个或多个检查点的虚拟机。*

## <a name="impact"></a>影响

*可用空间可能会在存储检查点文件的物理磁盘上运行。如果发生这种情况，则不能在物理存储上执行其他磁盘操作。依赖于物理存储的任何虚拟机都可能会受到影响。*

如果物理磁盘空间不足，则在该磁盘上存储的检查点或虚拟硬盘的任何正在运行的虚拟机可能会自动暂停。 Hyper-v 管理器将这些虚拟机的状态显示为 "暂停-关键"。

## <a name="resolution"></a>解决方法

*如果虚拟机在生产环境中运行服务器工作负荷，则使虚拟机脱机，并使用 Hyper-v 管理器应用或删除检查点。若要删除检查点，你必须关闭虚拟机以完成该过程。*

> [!NOTE]
> 现在，可以使用生产检查点作为标准检查点的替代方案。 有关详细信息，请参阅[在标准或生产检查点之间选择](../manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md)。