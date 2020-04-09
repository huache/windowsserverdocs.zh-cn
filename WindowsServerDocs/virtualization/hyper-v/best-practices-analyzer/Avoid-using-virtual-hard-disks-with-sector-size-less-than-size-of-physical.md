---
title: 避免使用其扇区大小小于存储虚拟硬盘文件的物理存储扇区大小的虚拟硬盘
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: b7cf994e-bf4b-4b1b-bad6-ecf7d46d105e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: f7ea02ab83d3d896d2ad3681526133e23725b819
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857700"
---
# <a name="avoid-using-virtual-hard-disks-with-a-sector-size-less-than-the-sector-size-of-the-physical-storage-that-stores-the-virtual-hard-disk-file"></a>避免使用其扇区大小小于存储虚拟硬盘文件的物理存储扇区大小的虚拟硬盘

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。  
  
|属性|详细信息|  
|-|-|  
|**经营** <br />**主板**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**对应**|警告|  
|**类别**|配置|  
  
在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。  
  
## <a name="issue"></a>**问题**  
*一个或多个虚拟硬盘的物理扇区大小小于虚拟硬盘文件所在存储区的物理扇区大小。*  
  
## <a name="impact"></a>**对**  
*使用虚拟硬盘的虚拟机或应用程序可能会出现性能问题。这会影响以下虚拟机：*  
  
虚拟机 \<列表 >  
  
## <a name="resolution"></a>**解决方法**  
*执行下列操作之一：*  
  
-   *执行存储迁移，将虚拟硬盘移动到新的物理系统*  
  
-   *使用 Windows PowerShell 或 WMI 启用 VHDX 格式的虚拟硬盘，以报告特定扇区大小*  
  
-   *使用注册表设置来启用 VHD 格式的虚拟硬盘，以报告4k 的物理扇区大小*  
  


