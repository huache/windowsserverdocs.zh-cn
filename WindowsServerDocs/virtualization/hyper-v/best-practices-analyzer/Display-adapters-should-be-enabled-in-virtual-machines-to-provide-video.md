---
title: 应在虚拟机中启用显示适配器以提供视频功能
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: ac5992e6-3c0b-46c2-a48e-6ef37b679228
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 1821aae18b1712ba7d839ca9f42318edc5ef8a35
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80862000"
---
# <a name="display-adapters-should-be-enabled-in-virtual-machines-to-provide-video-capabilities"></a>应在虚拟机中启用显示适配器以提供视频功能

>适用于：Windows Server 2016


  
有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。  
  
|属性|详细信息|  
|-|-|  
|**操作系统**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**对应**|警告|  
|**类别**|配置|  
  
在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。  
  
## <a name="issue"></a>问题  
  
*Microsoft 虚拟机总线视频设备可能在虚拟机中处于禁用状态。*  
  
Microsoft 虚拟机总线视频设备是一种优化了用于 Hyper-v 虚拟机的虚拟视频适配器。 如果未将虚拟机配置为使用 Microsoft 虚拟机总线视频设备，将使用旧的视频适配器。 Microsoft 虚拟机总线视频设备的性能优于传统的视频适配器。  
  
## <a name="impact"></a>影响  
  
*以下虚拟机的视频性能将会降级：*  
  
虚拟机名称 \<列表 >  
  
## <a name="resolution"></a>分辨率  
  
*使用来宾操作系统中的设备管理器来启用 Microsoft 虚拟机总线视频设备。*  
  
使用设备管理器所需的步骤因操作系统而异。 有关说明，请参阅来宾操作系统中的帮助。  
  


