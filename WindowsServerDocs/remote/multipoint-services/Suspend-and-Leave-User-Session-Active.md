---
title: 挂起用户会话并使其保持为活动状态
description: 了解如何在无需断开连接的情况下从 MultiPoint 会话中挂起用户
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 5263bce3-fe92-4398-8393-2e3a4e05d530
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 2d2771fd60f4d8c11c602a4c5d55f3b5ae2d8b11
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861620"
---
# <a name="suspend-and-leave-user-session-active"></a>挂起用户会话并使其保持为活动状态
当你不想结束用户的会话时，你可以断开或挂起用户的 MultiPoint 服务系统。 无需你为其断开会话，用户也可自主断开会话。 暂停用户会话时，会话将在 MultiPoint 服务系统的计算机内存中保持活动状态，直到关闭或重新启动计算机。 一旦关闭或重启计算机，所有挂起的会话都将结束，并且任何未保存的工作都将丢失。  
  
1.  在工作站模式下打开 "MultiPoint 管理器"，然后单击 "**工作站**" 选项卡。  
  
2.  在“计算机”列中，单击想要挂起其会话的计算机名称。  
  
3.  在“工作站任务”下，单击“挂起所有工作站”。  
  
挂起用户会话后，用户可以登录到相同或另一个工作站，并可在原始会话中继续工作。  
  
## <a name="see-also"></a>另请参阅  
[管理用户桌面](manage-user-desktops-using-multipoint-dashboard.md)  
[注销或断开用户会话](Log-off-or-Disconnect-User-Sessions.md)