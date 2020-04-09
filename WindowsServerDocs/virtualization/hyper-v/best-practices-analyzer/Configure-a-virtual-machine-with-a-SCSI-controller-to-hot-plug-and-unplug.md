---
title: 配置具有 SCSI 控制器的虚拟机，使其能够热插拔存储
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 511e1172-aeef-463d-b5dd-2bffae411ff1
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: bd49a911d278a1f07fe9630f39798204d760dd88
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80862150"
---
# <a name="configure-a-virtual-machine-with-a-scsi-controller-to-be-able-to-hot-plug-and-hot-unplug-storage"></a>配置具有 SCSI 控制器的虚拟机，使其能够热插拔存储

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
  
*找到了未配置 SCSI 控制器的虚拟机。*  
  
## <a name="impact"></a>影响  
  
*对于下列虚拟机，你将无法热插拔或热拔下存储：*  
  
虚拟机名称 \<列表 >  
  
使用热插拔存储的功能，可更轻松地管理虚拟机的存储需求，而无需停机。 必须先关闭没有 SCSI 控制器的虚拟机，然后才能添加或删除存储。  
  
## <a name="resolution"></a>分辨率  
  
*如果不需要热插拔此虚拟机的存储，则无需执行任何操作。否则，请关闭虚拟机，并向配置中添加 SCSI 控制器。*  
  
若要使用 SCSI 控制器来热插拔存储，来宾操作系统必须运行当前版本的 integration services。  
  


