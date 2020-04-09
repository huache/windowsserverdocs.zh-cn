---
ms.assetid: 6e711a96-9055-4508-b6d4-318d6aa95fd1
title: 何时使用身份委派
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 7a594332900c8b3afb95c139bcde8458a10f186b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858460"
---
# <a name="when-to-use-identity-delegation"></a>何时使用身份委派
  
## <a name="what-is-identity-delegation"></a>什么是身份委派？  
标识委派是 Active Directory 联合身份验证服务 \(AD FS\) 的一项功能，该功能允许管理员\-指定的帐户来模拟用户。 模拟用户的帐户称为“代理人”。 对于要为其进行一系列访问控制检查并且必须为处于原始请求的授权链中的每个应用程序、数据库或服务按顺序进行这些检查的许多分布式应用程序，此委派功能至关重要。 许多实际\-世界方案存在，其中的 Web 应用程序 "前端" 必须从更安全的 "后端" （如连接到 Microsoft SQL Server 数据库的 Web 服务）检索数据。  
  
例如，可以以编程方式增强\-排序网站的现有部分，使合作伙伴组织能够查看其自己的购买历史记录和帐户状态。 出于安全原因，所有合作伙伴财务数据都存储在专用结构化查询语言 \(SQL\) 服务器上的安全数据库中。 在这种情况下，\-前端应用程序中的代码不知道有关合作伙伴组织财务数据的任何信息。 因此，它必须从位于 \(网络上其他位置的另一台计算机上检索该数据，该计算机在这种情况下\) \(后端\)part 数据库的 Web 服务。  
  
为了使此数据\-检索过程成功，必须在 Web 应用程序和 Web 服务之间为 parts 数据库执行一些后续的授权 "手型\-握手"，如下图所示。  
  
![标识委派](media/adfs2_identitydelegationconcept.gif)  
  
因为原始请求是对 Web 服务器本身进行的，而 Web 服务器可能位于与尝试访问 Web 服务器的用户的组织完全不同的组织中，所以随请求一起发送的安全令牌不符合访问除 Web 服务器之外的任何其他计算机所需的授权条件。 因此，可以实现原始用户请求的唯一方法是在资源伙伴组织中放置中间联合服务器，以帮助重新颁发没有适当访问权限的安全令牌。  
  
## <a name="how-does-identity-delegation-work"></a>身份委派是如何工作的？  
多层应用程序体系结构中的 Web 应用程序通常调用 Web 服务来访问公共数据或功能。 这些 Web 服务应了解原始用户的身份，以便服务可以进行授权决策并便于审核，这十分重要。 在这种情况下，前端 Web 应用程序的\-将用户作为委托表示给 Web 服务。 AD FS 通过允许 Active Directory 帐户作为另一方的用户来实现此方案。 身份委派方案如下图所示。  
  
![标识委派](media/adfs2_identitydelegationsteps.gif)  
  
1.  Frank 尝试从其他组织中的 Web 应用程序访问部分\-排序历史记录。 他的客户端计算机请求并接收来自前\-结束部分\-订购 Web 应用程序 AD FS 的令牌。  
  
2.  客户端计算机将请求发送到 Web 应用程序（包括在步骤1中获取的令牌）以证明客户端的标识。  
  
3.  Web 应用程序需要与 Web 服务进行通信来为客户端完成事务。 Web 应用程序与 AD FS 联系以获取用于与 Web 服务进行交互的委派令牌。 委派令牌是颁发给代理人以充当用户的安全令牌。 AD FS 返回包含有关客户端的声明的委派令牌，针对的是 Web 服务。  
  
4.  Web 应用程序使用在步骤3中 AD FS 获取的令牌来访问充当客户端的 Web 服务。 通过检查委派令牌，Web 服务可以确定 Web 应用程序在充当客户端。 Web 服务执行其授权策略，记录请求，并将最初由 Frank 请求的所需零件历史记录数据提供给 Web 应用程序，因而提供给 Frank。  
  
对于特定委托，AD FS 可以限制 Web 应用程序可以为其请求委派令牌的 Web 服务。 客户端计算机不必具有 Active Directory 帐户即可成功执行此操作。 最后，如前所述，Web 服务可以轻松确定充当用户的代理人的身份。 这允许 Web 服务基于它们是直接与客户端计算机进行通信还是通过代理人来展示不同的行为。  
  
## <a name="configuring-ad-fs-for-identity-delegation"></a>为身份委派配置 AD FS  
你可以使用中的 AD FS 管理 "管理单元\-为标识委派配置 AD FS，只要你需要加速数据检索过程即可。 配置后，AD FS 可能会生成新的安全令牌，其中将包括后端\-结束服务在可以提供对受保护数据的访问之前可能需要的授权上下文。  
  
AD FS 不限制可以模拟的用户。 为标识委派配置 AD FS 后，它将执行以下操作：  
  
-   它确定可以向颁发机构委派哪些服务器以请求令牌来模拟用户。  
  
-   它为委派的客户端帐户和充当代理人的服务器建立并保留单独的身份上下文。  
  
可以通过将委派授权规则添加到中 AD FS 管理 "管理单元\-中的信赖方信任来配置身份委派。 有关如何执行此操作的详细信息，请参阅 [Checklist: Creating Claim Rules for a Relying Party Trust](../../ad-fs/deployment/Checklist--Creating-Claim-Rules-for-a-Relying-Party-Trust.md)。  
  
## <a name="configuring-the-front-end-web-application-for-identity-delegation"></a>为标识委派配置前端 Web 应用程序\-  
开发人员有几个选项可用于适当地对 Web 前端\-最终应用程序或服务进行编程，以将委派请求重定向到 AD FS 的计算机。 有关如何自定义 Web 应用程序以使用身份委派的详细信息，请参阅 [Windows Identity Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
