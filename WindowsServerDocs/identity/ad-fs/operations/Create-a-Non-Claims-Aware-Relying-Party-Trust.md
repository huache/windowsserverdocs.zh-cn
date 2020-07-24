---
ms.assetid: 7b7ae389-5032-44f7-9c0a-94398c3e4d88
title: 创建非声明感知信赖方信任
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 2bc08d2797812d6001f2a792037bcfb8bab4fc0a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965639"
---
# <a name="create-a-non-claims-aware-relying-party-trust"></a>创建非声明感知信赖方信任


在 AD FS 管理 "管理单元 \- 中，非 \- 声明 \- 感知信赖方信任是创建的对象，用于表示联合身份验证服务与 \- 不是声明 \- 感知并通过 web 应用程序代理访问的单个基于 web 的应用程序之间的信任。  
  
非 \- 声明 \- 感知信赖方信任是信赖方信任，它由标识符、名称和用于身份验证和授权的规则组成，在通过 Web 应用程序代理访问信赖方信任时进行身份验证和授权。 这些基于 web 的 \- 应用程序不依赖于声明，换言之，这些基于 Windows 身份验证的基于 Windows 身份验证的 \- 应用程序可以具有授权规则，这些规则会在通过 Web 应用程序代理访问企业网络外部时强制实施基于声明的访问。  
  
若要添加新的非 \- 声明 \- 感知信赖方信任，请使用中的 AD FS 管理 "管理单元 \- ，然后执行以下过程。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。   
  
## <a name="to-create-a-non-claims-aware-relying-party-trust-manually"></a>手动创建非声明感知信赖方信任 
1. 在服务器管理器中，单击“工具”，选择“AD FS 管理”********。  
  
2.  在 "**操作**" 下，单击 "**添加信赖方信任**"。  
![信赖方](media/Create-a-Relying-Party-Trust/addtrust1.PNG)   

3.  在**欢迎**页上，选择 "**不感知声明**"，然后单击 "**启动**"。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon1.PNG) 
  
4.  在“指定显示名称”**** 页上的“显示名称”**** 中键入一个名称，在“说明”**** 下键入有关此信赖方信任的描述，然后单击“下一步”****。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon2.PNG)

5. 在“配置标识符”**** 页上，为此信赖方指定一个或多个标识符、单击“添加”**** 以将其添加到列表中，然后单击“下一步”****。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon3.PNG)

6.  在“选择访问控制策略”**** 上选择一个策略，然后单击“下一步”****。  有关访问控制策略的详细信息，请参阅[AD FS 中的访问控制策略](Access-Control-Policies-in-AD-FS.md)。 
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon4.PNG)

7. 在“准备好添加信任”**** 页上，复查设置，然后单击“下一步”**** 来保存信赖方信任的信息。  
   ![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon5.PNG) 

8. 在“完成”**** 页面上，单击“关闭”****。 执行此操作会自动显示“编辑声明规则”对话框****。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon6.PNG)  
  
## <a name="see-also"></a>另请参阅  
[AD FS 操作](../ad-fs-operations.md) 
