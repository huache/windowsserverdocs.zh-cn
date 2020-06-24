---
title: 添加 Microsoft Online Services 合作伙伴协议记录的合作伙伴信息
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 9bd191d6-ecc5-4230-a88e-f3fc281cb956
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 8b397a8fd2047c1a6fcaf5de2f5e1af167f1029f
ms.sourcegitcommit: 6d6a0225b1f83b71fcb494b94d666cd5e54c7566
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85267448"
---
# <a name="add-microsoft-online-service-partner-agreement-partner-of-record-information"></a>添加 Microsoft Online Services 合作伙伴协议记录的合作伙伴信息

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_3rdLevelDomanNames"></a>   
 如果你是 Office 365 的 Microsoft 联机服务合作伙伴协议（MOSPA）合作伙伴，则为了确保你在通过 Office 365 集成模块从 Windows Server Essentials 发起订阅请求时得到正确补偿，你需要创建一个包含记录的合作伙伴标识（POR ID）的注册表项。 以下信息将通过 Office 365 注册 URL 读取并传达给服务提供商。  
  
-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO  
  
-   类型 = 字符串值  
  
-   项名 = Partner  
  
-   值 = xxxxx（你的 POR ID）  
  
#### <a name="to-add-the-por-id-key-to-the-registry"></a>向注册表添加 POR ID 项  
  
1.  在引用计算机上，单击 **“开始”**，键入 **regedit**，然后按 Enter 键。  
  
2.  在左侧窗格中，依次展开 **“HKEY_LOCAL_MACHINE”**、**“SOFTWARE”**、**“Microsoft”** 和 **“Windows Server”**。  
  
3.  右键单击 **“Windows Server”**，指向 **“新建”**，然后单击 **“项”**。  
  
4.  输入 **“MSO”** 作为该项的名称。  
  
5.  右键单击刚刚创建的项，然后单击 **“字符串值”**。  
  
6.  输入 **“Partner”** 作为字符串的名称，然后按 ENTER。  
  
7.  在右侧窗格中，右键单击新的 **“Partner”** 字符串，然后单击 **“修改”**。  
  
8.  在 **“值数据”** 文本框中输入你的 POR ID，然后单击 **“确定”**。  
  
## <a name="see-also"></a>另请参阅  

 [创建和自定义映像](Creating-and-Customizing-the-Image.md)   
 [其他自定义](Additional-Customizations.md)   
 [准备要部署的映像](Preparing-the-Image-for-Deployment.md)   
 [测试客户体验](Testing-the-Customer-Experience.md)

