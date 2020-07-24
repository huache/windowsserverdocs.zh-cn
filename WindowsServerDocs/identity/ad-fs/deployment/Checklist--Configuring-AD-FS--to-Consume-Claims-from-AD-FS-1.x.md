---
ms.assetid: e7f9e518-2d5d-4a0d-9147-34e1304f42ac
title: 清单-配置 AD FS 以使用 AD FS 1.x 中的声明
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: b78dbdcd06bfd3801c17491156cfb0aaf81a2a9d
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86960359"
---
# <a name="checklist-configuring-ad-fs--to-consume-claims-from-ad-fs-1x"></a>清单︰ 配置 AD FS 以使用声明从 AD FS 1.x

  
## <a name="checklist-configuring-ad-fs-to-consume-claims-from-adfs1x"></a>清单：配置 AD FS 以使用 AD FS 1.x 中的声明  
此清单包括配置 Active Directory 联合身份验证服务所需的任务 \(AD FS\) Windows Server 2012 使用由 AD FS 1 发送的声明中的联合身份验证服务。*x* 联合身份验证服务。  
  
> [!NOTE]  
> 请按顺序完成本清单中的任务。 当某个参考连接将你转至某个过程时，应在完成该过程中的步骤之后返回此主题，以便你可以继续执行此清单中的其他任务。  
  
![使用 AD FS 清单中的声明](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**：配置 AD FS 以使用 AD FS 1.x 中的声明**  
  
||任务|参考|  
|-|--------|-------------|  
|![使用从 AD FS 声明](media/icon_checkboxo.gif)|Windows Server 2012 中的 AD FS 和以前版本的 AD FS 之间的互操作性规划和了解更多有关名称 ID 声明类型。|![使用](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS 1.x 的互操作性 AD FS 计划中的](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678040(v=ws.11))声明|  
|![使用从 AD FS 声明](media/icon_checkboxo.gif)|可以与以前版本的 AD FS 进行互操作之前，必须首先创建声明提供方信任 AD FS 联合身份验证服务中。 **注意︰** 不能使用 AD FS 1 创建了信任关系。*x* 使用联合身份验证元数据的联合身份验证服务。<p>如果您设置了信任关系使用右侧的链接中的过程，必须执行以下操作中添加声明提供方信任向导设置此信任，以与 AD FS 1 进行互操作。*x* 联合身份验证服务︰<p>1. 在 "**选择数据源**" 页上，选择 **"手动输入信赖方信任的数据"**。<br />2. 在 "**选择配置文件**" 页上，选择**AD FS 1.0 和1.1 配置文件**。<br />3. 在 "**配置 URL** " 页上的 " **WS \- 联合身份验证被动 URL**" 下，键入 AD FS 1 中定义的**联合身份验证服务终结点 URL** 。*x*联合身份验证服务。<br />4. 在 "**配置标识符**" 页上的 "**声明提供方信任标识符**" 下，键入 AD FS 1 中定义的**联合身份验证服务 URI** 。*x*联合身份验证服务。|![使用中的声明](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[手动创建声明提供方信任](../../ad-fs/operations/Create-a-Claims-Provider-Trust.md)AD FS|  
|![使用从 AD FS 声明](media/icon_checkboxo.gif)|在以前创建声明提供方信任，您必须创建一个声明规则，将会从 AD FS 传入声明 1.x 联合身份验证服务和传递，筛选，或者通过将其转换为名称 ID 声明类型。<p>当名称 ID 声明类型传递，通过筛选，或转换，它可以用作输入到另一个规则或规则，以便它可以理解并由 Windows Server 2012 中 AD FS 联合身份验证服务。|![使用 AD FS 中的声明](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[创建一个规则以发送 AD FS 1.X 兼容声明](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)|  
|![使用从 AD FS 声明](media/icon_checkboxo.gif)|AD FS 1 的管理员联系。*x* 联合身份验证服务和 AD FS 1 与系统管理员。*x* 联合身份验证服务建立的新资源伙伴信任。 此外，该管理员提供联合身份验证服务 URI \(联合身份验证服务属性中\), ，联合身份验证服务终结点 URL，并导出的令牌\-签名证书文件 \(仅公共密钥与\)。 管理员将需要这些项目以设置信任。|N\/A|  
  
