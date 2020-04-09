---
title: 对于运行 Hyper-v 的服务器，建议使用域成员身份
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 2f4578e5-0848-46b4-a50b-7dbd480b80bf
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: de38374a127a15c2a1d4bf262b72781429fa477c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861990"
---
# <a name="domain-membership-is-recommended-for-servers-running-hyper-v"></a>对于运行 Hyper-v 的服务器，建议使用域成员身份

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
  
*此服务器是工作组的成员。*  
  
## <a name="impact"></a>影响  
  
*此服务器没有中心管理。*  
  
如果将此计算机加入域，则可以通过策略进行集中管理，以实现标识、安全性和审核。  
  
## <a name="resolution"></a>分辨率  
  
*如果你有可用的域环境，请将此服务器加入该域。*  
  
> [!IMPORTANT]  
> 建议你查看在此计算机上的虚拟机中运行的工作负荷，以确定是否存在将此计算机加入到域的安全隐患。 如果有任何虚拟机为虚拟化域控制器，请参阅[规划虚拟化域控制器（ https://go.microsoft.com/fwlink/?LinkId=190192)的注意事项](https://go.microsoft.com/fwlink/?LinkId=190192)。  
  
将计算机加入到域需要计算机和域的权限：   
- 在计算机上，你将需要一个用户帐户，该帐户是 Administrators 组的成员。 请用此类型的帐户登录，或在出现提示时提供帐户的用户名和密码。   
- 在域上，你将需要一个用户帐户，该帐户有权将计算机加入域。 系统将提示你输入用户名和密码。  
  
有关说明，请参阅将[计算机加入到域](https://go.microsoft.com/fwlink/?LinkId=190193)（ https://go.microsoft.com/fwlink/?LinkId=190193)。  
  


