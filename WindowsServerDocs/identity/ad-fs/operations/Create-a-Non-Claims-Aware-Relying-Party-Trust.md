---
ms.assetid: 7b7ae389-5032-44f7-9c0a-94398c3e4d88
title: 创建非声明感知信赖方信任
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b0ea877170a07db6abe9ac82e72d1722600ec933
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358108"
---
# <a name="create-a-non-claims-aware-relying-party-trust"></a>创建非声明感知信赖方信任


在中的 AD FS 管理 "管理单元\-中，非\-声明\-感知信赖方信任是创建的对象，用于表示联合身份验证服务与不是声明\-感知的单个基于 web\-的应用程序之间的信任，并通过 Web 应用程序代理进行访问。  
  
不\-声明\-感知信赖方信任是信赖方信任，它由标识符、名称和用于身份验证和授权的规则组成，在通过 Web 应用程序代理访问信赖方信任时进行身份验证和授权。 这些基于 web\-的应用程序，这些应用程序不依赖于声明，换言之，这些基于 Windows 身份验证\-的应用程序，可以在通过 Web 应用程序代理访问企业网络外部时，使用授权规则来强制实施基于声明的访问。  
  
若要添加新的非\-声明\-感知信赖方信任，请使用中的 AD FS 管理 "管理单元\-，执行以下过程。  
  
本地计算机上的 **Administrators** 中的成员身份或等效身份是完成这些过程所需的最低要求。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
## <a name="to-create-a-non-claims-aware-relying-party-trust-manually"></a>手动创建非声明感知信赖方信任 
1. 在服务器管理器中，单击 "**工具**"，然后选择 " **AD FS 管理**"。  
  
2.  在 "**操作**" 下，单击 "**添加信赖方信任**"。  
![信赖方](media/Create-a-Relying-Party-Trust/addtrust1.PNG)   

3.  在**欢迎**页上，选择 "**不感知声明**"，然后单击 "**启动**"。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon1.PNG) 
  
4.  在 "**指定显示名称**" 页上，在 "**显示名称**" 中的 "**备注**" 下键入此信赖方信任的描述，然后单击 "**下一步**"。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon2.PNG)

5. 在“配置标识符”页上，为此信赖方指定一个或多个标识符、单击“添加”以将其添加到列表中，然后单击“下一步”。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon3.PNG)

6.  在 "**选择访问控制策略**" 中选择一个策略，然后单击 "**下一步**"。  有关访问控制策略的详细信息，请参阅[AD FS 中的访问控制策略](Access-Control-Policies-in-AD-FS.md)。 
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon4.PNG)

7. 在“准备好添加信任” 页上，复查设置，然后单击“下一步” 来保存信赖方信任的信息。  
   ![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon5.PNG) 

8. 在“完成”页面上，单击“关闭”。 执行此操作会自动显示“编辑声明规则”对话框。  
![信赖方](media/Create-a-Non-Claims-Aware-Relying-Party-Trust/addnon6.PNG)  
  
## <a name="see-also"></a>另请参阅  
[AD FS 操作](../../ad-fs/AD-FS-2016-Operations.md) 
