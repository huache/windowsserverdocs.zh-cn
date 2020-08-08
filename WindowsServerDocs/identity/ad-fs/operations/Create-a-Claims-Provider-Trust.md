---
ms.assetid: a4f7842c-cfca-4d78-916e-023d12a9cdf0
title: 创建声明提供方信任
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 223e2b368ecd7fe3031cedced5b9fac0d4c5ba9a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87967554"
---
# <a name="create-a-claims-provider-trust"></a>创建声明提供方信任

若要使用 AD FS 管理 "管理单元添加新的声明提供方信任 \- 并手动配置设置，请在资源伙伴组织中的资源伙伴联合服务器上执行以下过程。

在本地计算机上， **Administrators**中的成员身份或同等身份是完成此过程的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

## <a name="to-create-a-claims-provider-trust-manually"></a>手动创建声明提供方信任的步骤

1.  在服务器管理器中，单击“工具”，选择“AD FS 管理”********。

2.  在 "**操作**" 下，单击 "**添加声明提供方信任**"。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim1.PNG)

3.  在“欢迎使用”**** 页面上，单击“启动”****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim2.PNG)

4.  在“选择数据源”**** 页面上，单击“手动输入声明提供方信任数据”****，然后单击“下一步”****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim3.PNG)

5.  在“指定显示名称”页面上**** 键入一个显示名称****，在“注释”**** 下键入此声明提供方信任的描述，然后单击“下一步”****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim4.PNG)

6.  在 "**配置 URL** " 页面上，指定**WS 联合身份验证被动 URL** （如果适用），然后单击 "**下一步**"。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim5.PNG)

8. 在“配置标识符”页面上的“声明提供方信任标识符”下，******** 键入相应的标识符，然后单击“下一步”****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim6.PNG)

9. 在“配置证书”页面上，单击“添加”找到证书文件并将它添加到证书列表，然后单击“下一步”************。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim7.PNG)

10. 在“准备好添加信任”页面上，**** 单击“下一步”保存声明提供方信任信息****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim8.PNG)

11. 在“完成”**** 页面上，单击“关闭”****。 执行此操作会自动显示“编辑声明规则”对话框****。 有关如何继续添加此声明提供方信任的声明规则的详细信息，请参阅以下附加引用。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim9.PNG)

## <a name="to-create-a-claims-provider-trust-using-federation-metadata"></a>使用联合元数据创建声明提供方信任
若要添加新的声明提供方信任，请使用 AD FS 管理单元，通过从合作伙伴发布到本地网络或 Internet 的联合元数据自动导入有关伙伴的配置数据，请在资源伙伴组织中的联合服务器上执行以下过程。

>[!NOTE]
>尽管使用具有非限定主机名（如 https：/myserver）的证书通常很常见 \/ ，但这些证书没有安全价值，并且可以使攻击者模拟正在发布联合元数据的联合身份验证服务。 因此，在查询联合元数据时，只应使用完全限定的域名，如 `https://myserver.contoso.com` 。

1.  在服务器管理器中，单击“工具”，选择“AD FS 管理”********。

2.  在 "**操作**" 下，单击 "**添加声明提供方信任**"。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim1.PNG)

3.  在“欢迎使用”**** 页面上，单击“启动”****。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim2.PNG)

4.  在“选择数据源”页面上，**** 单击“导入有关在线或在本地网络上发布的声明提供方的数据”****。 在 "联合元数据地址 (主机名或 URL") 中，键入伙伴的**联合元数据 URL**或主机名，然后单击 "**下一步**"。
![声明提供方信任](media/Create-a-Claims-Provider-Trust/addclaim10.PNG)

5.  在 "指定显示名称" 页上，键入**显示名称**，在 "注释" 中键入此声明提供方信任的描述，然后单击 "**下一步**"。

6.  在 "准备添加信任" 页上，单击 "**下一步**" 以保存声明提供程序信任信息。

7.  在“完成”  页面上，单击“关闭” ****。 这会自动显示 "编辑声明规则" 对话框。 有关如何继续为此声明提供方信任添加声明规则的详细信息，请参阅下面的 "其他参考" 部分。




## <a name="additional-references"></a>其他参考
[清单︰ 配置资源伙伴组织](../../ad-fs/deployment/Checklist--Configuring-the-Resource-Partner-Organization.md)

[清单：为声明提供方信任创建声明规则](../../ad-fs/deployment/Checklist--Creating-Claim-Rules-for-a-Claims-Provider-Trust.md)

## <a name="see-also"></a>另请参阅
[AD FS 操作](../ad-fs-operations.md)

