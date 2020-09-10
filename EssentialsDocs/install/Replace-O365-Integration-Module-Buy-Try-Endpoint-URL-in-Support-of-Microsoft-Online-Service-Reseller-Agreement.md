---
title: 替换 Microsoft 365 集成模块购买-尝试终结点 URL 以支持 Microsoft Online Services 经销商协议
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 9860a6b9-baea-4bf0-9a9f-6f1a288f996e
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: a8a5cf91c6de2971bc8270cc3c7ea92327b71224
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623375"
---
# <a name="replace-microsoft-365-integration-module-buy-try-endpoint-url-in-support-of-microsoft-online-service-reseller-agreement"></a>替换 Microsoft 365 集成模块购买-尝试终结点 URL 以支持 Microsoft Online Services 经销商协议

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_O365"></a>
 如果你是 (MOSRA) 合作伙伴的 Microsoft 联机服务经销商协议，若要确保通过你的门户处理客户注册交易，你将需要替换 Windows Server Essentials Microsoft 365 集成模块使用的终结点 Url。

 集成模块使用以下四个终结点 URL：

1.  Microsoft 365 企业版订阅购买终结点。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\

    -   类型 = REG-SZ

    -   项名 = MOSRASTDBUY

    -   值 = *xxxxx*，其中 xxxxx 是你的企业订阅购买 URL。 例如，Value = http://syndicatepartner.office365.com/enterprisebuy.html

2.  Microsoft 365 企业版订阅试用终结点。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\

    -   类型 = REG-SZ

    -   项名 = MOSRASTDTRY

    -   值 = *xxxxx*，其中 xxxxx 是你的企业订阅购买 URL。 例如，Value = http://syndicatepartner.office365.com/enterprisetry.html

3.  Microsoft 365 小型企业高级订阅购买终结点。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\

    -   类型 = REG-SZ

    -   项名 = MOSRALITEBUY

    -   值 = *xxxxx*，其中 xxxxx 是你的企业订阅购买 URL。 例如，Value = http://syndicatepartner.office365.com/smallbizbuy.html

4.  Microsoft 365 小型企业高级订阅试用终结点。

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\

    -   类型 = REG-SZ

    -   项名 = MOSRALITETRY

    -   值 = *xxxxx*，其中 xxxxx 是你的企业订阅购买 URL。 例如，Value = http://syndicatepartner.office365.com/smallbiztry.html

#### <a name="to-add-an-endpoint-url-key-to-the-registry"></a>向注册表添加终结点 URL 项

1.  在引用计算机上，单击 **“开始”**，键入 **regedit**，然后按 Enter 键。

2.  在左侧窗格中，依次展开 **“HKEY_LOCAL_MACHINE”**、**“SOFTWARE”**、**“Microsoft”**、**“Windows Server”** 和 **“MSO”**。

3.  如果 MSO 不存在，则右键单击 **“Windows Server”**，指向 **“新建”**，单击 **“项”**，然后键入 **MSO** 作为该项的名称。

4.  右键单击 MSO，然后单击 **“字符串值”**。 输入以下终结点字符串名称之一作为字符串的名称：

    -   MOSRASTDBUY

    -   MOSRASTDTRY

    -   MOSRALITEBUY

    -   MOSRALITETRY

5.  右键单击右侧窗格中的新字符串，然后单击 **“修改”**。

6.  在 **“值数据”** 文本框中输入新的终结点 URL，然后单击 **“确定”**。

7.  对步骤 4 中列出的每个字符串名称重复步骤 4-6。

## <a name="see-also"></a>另请参阅

 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)

