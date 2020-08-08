---
ms.assetid: 4b81ac66-3f34-4a39-a8bf-5411131a69c2
title: 清单-配置 AD FS 以使用 AD FS 1.x 中的声明
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 27965c489b1f4a678d7d6212eb858b094b050dc3
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969754"
---
# <a name="checklist-configuring-ad-fs-to-send-claims-to-an-ad-fs-1x-federation-service"></a>清单︰ 配置 AD FS 以发送到 AD FS 1.x 联合身份验证服务的声明


## <a name="checklist-configuring-ad-fs-to-send-claims-to-an-adfs1x-federation-service"></a>清单：配置 AD FS 向 AD FS 1.x 联合身份验证服务发送声明
此清单包括配置 Active Directory 联合身份验证服务所需的任务 \(AD FS\) 发送声明可以理解的 AD FS 1 的 Windows Server 2012 中的联合身份验证服务。*x* 联合身份验证服务。

> [!NOTE]
> 请按顺序完成本清单中的任务。 当某个参考连接将你转至某个过程时，应在完成该过程中的步骤之后返回此主题，以便你可以继续执行此清单中的其他任务。

![配置 AD FS 以发送声明](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**清单：配置 AD FS 将声明发送到 AD FS 1.x 联合身份验证服务**

|任务|参考|
|--------|-------------|
|规划 Windows Server 2012 和早期版本的 AD FS 中 AD FS 之间的互操作性，并详细了解名称 ID 声明类型。|![配置 AD FS 以便发送](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[与 AD FS 1.X 互操作性的声明规划](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678040(v=ws.11))|
|您可以实现与以前版本的 AD FS 互操作性之前，必须首先创建到 AD FS 1 的 AD FS 联合身份验证服务中的信赖方信任。*x* 联合身份验证服务。 **注意︰** 不能使用 AD FS 1 创建了信任关系。*x* 使用联合身份验证元数据的联合身份验证服务。<p>如果您设置了信任关系使用右侧的链接中的过程，必须执行以下操作添加信赖方信任向导中设置此信任，以与 AD FS 1 进行互操作。*x* 联合身份验证服务︰<p>1. 在 "**选择数据源**" 页上，选择 **"手动输入信赖方信任的数据"**。<br />2. 在 "**选择配置文件**" 页上，选择**AD FS 1.0 和1.1 配置文件**。<br />3. 在 "**配置 URL** " 页上的 " **WS \- 联合身份验证被动 URL**" 下，键入 AD FS 1 中定义的**联合身份验证服务终结点 URL** 。*x*联合身份验证服务。<br />4. 在 "**配置标识符**" 页上的 "**信赖部分信任标识符**" 下，键入 AD FS 1 中定义的**联合身份验证服务 URI** 。*x*联合身份验证服务。|![配置 AD FS 以发送声明](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[手动创建信赖方信任](../../ad-fs/operations/Create-a-Relying-Party-Trust.md)|
|在以前创建的信赖方信任，您必须创建声明规则，将需要从属性存储提取的传入声明和传递、 筛选或转换它们转换为名称 ID 声明类型可以理解和使用由 AD FS 1。*x* 联合身份验证服务。 **注意︰** 创建此规则之前，请确保在要创建此规则的声明规则集具有位于它之前它是第一次提取一种轻型目录访问协议的规则 \(LDAP\) 属性存储中的属性声明。 此声明将用作你创建的规则的输入，以发送 AD FS 1。*x* \-兼容声明。 有关如何创建一个规则以提取 LDAP 属性的详细信息，请参阅 [创建规则以声明方式发送 LDAP 属性](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)。|![配置 AD FS 以发送声明](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[创建一个规则以发送 AD FS 1.X 兼容声明](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)|
|AD FS 1 的管理员联系。*x* 联合身份验证服务和 AD FS 1 与系统管理员。*x* 设置新的帐户伙伴信任的联合身份验证服务。 此外，该管理员提供联合身份验证服务 URI \(联合身份验证服务属性中\), ，WS\-联合身份验证被动终结点 URL \(联合身份验证服务终结点 URL\), ，和一个导出的令牌\-签名证书文件 \(仅公共密钥与\)。 该管理员将需要这些项目以设置信任。|N\/A|

