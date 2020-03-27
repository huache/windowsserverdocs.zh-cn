---
title: 创建简单的自定义映像
description: 描述如何使用 Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29f9a09f-e4e8-476d-ada1-ab9202a670d7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 74a1729f9445710b6b9d279f1603295eff2a5d25
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80312130"
---
# <a name="create-a-simple-customized-image"></a>创建简单的自定义映像

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

可以使用以下过程创建简单的自定义映像：  
  
#### <a name="to-create-the-image"></a>创建映像  
  
1.  服务器安装完成后，在初始配置的第一页上，按 Shift+F10 来启动命令窗口。  
  
2.  在系统驱动器的根目录下创建 SkipIC.txt 文件。  
  
3.  重新启动服务器。  
  
4.  使用包含 unattend.xml 文件的 U 盘或 DVD 启动服务器。 有关创建可启动的 U 盘的信息，请参阅[创建可启动的 U 盘](Create-a-Bootable-USB-Flash-Drive.md)。  
  
5.  向仪表板添加徽标品牌。 有关添加品牌的详细信息，请参阅[向仪表板、远程 Web 访问和快速启动板添加品牌](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md)。  
  
6.  创建 OOBE.xml 文件以显示自定义信息，例如公司名称、徽标和 EULA。 有关 OOBE.xml 文件的详细信息，请参阅 [Create the Oobe.xml File Including Logo and EULA](Create-the-Oobe.xml-File-Including-Logo-and-EULA.md)。  
  
7.  如果未在 unattend.xml 中定义默认服务器名称，请更改该名称。  
  
8.  默认情况下，服务器名称为随机字符串。 将服务器名称更改为另一个字符串（如 ContosoServer），然后将新服务器名称通知给客户。  
  
9. 按[为进行部署准备映像](Preparing-the-Image-for-Deployment.md)中所述为进行部署准备映像。  
  
## <a name="see-also"></a>另请参阅  
 [入门 Windows Server ESSENTIALS ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)   
 [其他自定义](Additional-Customizations.md)   
 [准备映像以进行部署](Preparing-the-Image-for-Deployment.md)   
 [测试客户体验](Testing-the-Customer-Experience.md)