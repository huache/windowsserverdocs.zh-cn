---
title: 在将虚拟机配置为使用 SR-IOV 时，请确保虚拟函数驱动程序正常运行
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: d21e4b93-29bf-423a-a635-71c6d48dc49e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 282187d4d5a1243a14c3a0bdaa3088fe1f134bef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861920"
---
# <a name="ensure-that-the-virtual-function-driver-operates-correctly-when-a-virtual-machine-is-configured-to-use-sr-iov"></a>在将虚拟机配置为使用 SR-IOV 时，请确保虚拟函数驱动程序正常运行

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
*虚拟功能驱动程序在一个或多个虚拟机的来宾操作系统中运行不正常。*  
  
## <a name="impact"></a>影响  
*网络性能在以下虚拟机上不是最佳的：*  
  
虚拟机 \<列表 >  
  
## <a name="resolution"></a>分辨率  
*在来宾操作系统中，执行以下操作：验证是否安装了相应的驱动程序并启用了所有网络设备，并检查事件日志中是否存在错误或警告。*  
  


