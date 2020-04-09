---
title: 应从复制中排除包含页面文件的虚拟硬盘
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: c0be8a5f-64a1-488a-944e-bb913bb90517
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 94e03cf9de3991d003fad9019b9af33fad2f6bae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855020"
---
# <a name="virtual-hard-disks-with-paging-files-should-be-excluded-from-replication"></a>应从复制中排除包含页面文件的虚拟硬盘

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。  
  
|属性|详细信息|  
|-|-|  
|**操作系统**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**对应**|信息|  
|**类别**|配置|  
  
在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。  
  
## <a name="issue"></a>问题  
*应排除分页文件以参与复制，但不包括任何磁盘。*  
  
## <a name="impact"></a>影响  
*页面文件遇到大量的输入/输出活动，这将不必要地需要更多的资源来参与复制。这会影响以下虚拟机：*  
  
虚拟机 \<列表 >  
  
## <a name="resolution"></a>分辨率  
*如果尚未这样做，请为 Windows 页面文件创建一个单独的虚拟硬盘。如果初始复制已完成，请使用 Hyper-v 管理器删除复制。然后，再次配置复制，并从复制中排除包含页面文件的虚拟硬盘。*  
  


