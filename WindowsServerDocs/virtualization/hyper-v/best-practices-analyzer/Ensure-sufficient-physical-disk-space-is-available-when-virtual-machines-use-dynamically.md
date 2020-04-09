---
title: 当虚拟机使用动态扩展虚拟硬盘时，请确保有足够的物理磁盘空间可用
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 9e3e3e64-4b3a-4b9d-acf1-e4df61a04f1e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 53302d9e8fc4f960f0a1744d4ebd274b936eac5f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861940"
---
# <a name="ensure-sufficient-physical-disk-space-is-available-when-virtual-machines-use-dynamically-expanding-virtual-hard-disks"></a>当虚拟机使用动态扩展虚拟硬盘时，请确保有足够的物理磁盘空间可用

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。  
  
|属性|详细信息|  
|-|-|  
|**操作系统**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**对应**|警告|  
|**类别**|配置|  
  
在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。  
  
## <a name="issue"></a>问题  
*一个或多个虚拟机正在使用动态扩展的虚拟硬盘。*  
  
## <a name="impact"></a>影响  
*动态扩展虚拟硬盘需要主机卷上的可用空间，以便在写入虚拟硬盘时可以分配空间。如果可用空间已用完，则任何依赖于物理存储的虚拟机都可能会受到影响。这会影响以下虚拟机：*  
  
虚拟机 \<列表 >  
  
## <a name="resolution"></a>分辨率  
*监视可用磁盘空间，以确保有足够的空间可用于扩展。请考虑关闭虚拟机，并使用 Hyper-v 管理器中的编辑磁盘向导将此虚拟机的每个动态扩展的虚拟硬盘转换为固定大小的虚拟硬盘。*  
  


