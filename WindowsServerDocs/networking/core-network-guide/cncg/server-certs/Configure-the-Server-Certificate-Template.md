---
title: 配置服务器证书模板
description: 本主题是指导 802.1 X 有线和无线部署的 "部署服务器证书" 的一部分
manager: brianlic
ms.topic: article
ms.assetid: 8ff610e2-43ca-407f-a828-06d9366e02f0
ms.prod: windows-server
ms.technology: networking
ms.author: lizross
author: eross-msft
ms.openlocfilehash: fc4ba05466c2d87e6d6e9f7c0d5cee1bb405c79a
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318392"
---
# <a name="configure-the-server-certificate-template"></a>配置服务器证书模板

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用此过程来配置证书模板，该模板 Active Directory&reg; 证书服务（AD CS）用作注册到网络上服务器的服务器证书的基础。  
  
配置此模板时，可以通过 Active Directory 组来指定服务器，这些服务器应自动接收来自 AD CS 的服务器证书。   
  
以下过程包括有关配置模板以向以下所有服务器类型颁发证书的说明：  
  
- 运行远程访问服务的服务器，包括作为**ras 和 IAS 服务器**组成员的 Ras 网关服务器。  
- 运行网络策略服务器（NPS）服务的服务器，该服务是**RAS 和 IAS 服务器**组的成员。  
  
**企业管理员**和根域的**domain admins**组中的成员身份是完成此过程的最低要求。  
  
### <a name="to-configure-the-certificate-template"></a>配置证书模板  
  
1.  在 CA1 上的 "服务器管理器中，单击"**工具**"，然后单击"**证书颁发机构**"。 此时将打开证书颁发机构 "Microsoft 管理控制台（MMC）"。  
  
2.  在 MMC 中，双击 CA 名称，右键单击 "**证书模板**"，然后单击 "**管理**"。  
  
3.  此时将打开 "证书模板" 控制台。 所有证书模板将显示在详细信息窗格中。  
  
4.  在详细信息窗格中，单击 " **RAS 和 IAS 服务器**" 模板。  
  
5.  单击 "**操作**" 菜单，然后单击 "**复制模板**"。 此时将打开 "模板**属性**" 对话框。  
  
6.  单击“安全性”选项卡。   
  
7.  在 "**安全**" 选项卡上的 "**组或用户名**" 中，单击 " **RAS 和 IAS 服务器**"。  
  
8.  在 " **RAS 和 IAS 服务器的权限**" 下的 "**允许**" 下，确保已选择 "**注册**"，然后选择 "**自动注册**" 复选框。 单击 **"确定**"，然后关闭 "证书模板" MMC。  
  
9.  在证书颁发机构 MMC 中，单击 "**证书模板**"。 在 "**操作**" 菜单上，指向 "**新建**"，然后单击 "**要颁发的证书模板**"。 "**启用证书模板**" 对话框将打开。  
  
10. 在 "**启用证书模板**" 中，单击刚配置的证书模板的名称，然后单击 **"确定"** 。 例如，如果未更改默认证书模板名称，请单击 " **RAS 和 IAS 服务器的副本**"，然后单击 **"确定"** 。  
  


