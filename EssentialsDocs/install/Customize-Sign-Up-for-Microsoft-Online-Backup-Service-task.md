---
title: 自定义 Microsoft 联机备份任务的注册
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: a7eafbb3-7728-487e-b287-90bbd6fee7f0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 3318ca3937cdc054889121a830bc3eafec4d6acf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80818080"
---
# <a name="customize-sign-up-for-microsoft-online-backup-service-task"></a>自定义 Microsoft 联机备份任务的注册

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

默认情况下，仪表板 **“设备”** 选项卡上的 **“Microsoft 联机备份任务的注册”** 任务会打开 Microsoft 联机备份服务网站。 此网站提供有关服务的信息，并帮助你订阅服务和下载所需软件。  
  
 你可以通过两种方式自定义 **“Microsoft 联机备份任务的注册”** ：  
  
-   可以将默认网站的 URL 替换为表示自定义用户体验的 URL。 要替换默认 URL，请打开注册表编辑器，创建注册表项：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\LinkUrl**，然后分配自定义 URL 作为该注册表项的值。  
  
-   可以隐藏该任务。 若要隐藏该任务，请打开注册表编辑器并创建注册表项：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\OnlineBackupInstalled**。  
  
## <a name="see-also"></a>另请参阅  
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)   
 [其他自定义](Additional-Customizations.md)   
 [准备映像以进行部署](Preparing-the-Image-for-Deployment.md)   
 [测试客户体验](Testing-the-Customer-Experience.md)