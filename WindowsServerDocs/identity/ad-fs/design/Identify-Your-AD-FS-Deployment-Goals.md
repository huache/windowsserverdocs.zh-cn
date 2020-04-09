---
ms.assetid: c81b8291-fba5-4b30-a43d-7feb2f4b66be
title: Windows Server 2012 R2 中的 AD FS 设计指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 1bc898ba858cf49a71edcb89b10981d0bc8c1986
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853070"
---
# <a name="identify-your-ad-fs-deployment-goals"></a>标识 AD FS 部署目标

正确确定 Active Directory 联合身份验证服务 \(AD FS\) 部署目标对于 AD FS 设计项目的成功至关重要。 确定部署目标的优先级，并将其组合在一起，以便可以通过使用迭代方法来设计和部署 AD FS。 您可以利用与 AD FS 设计相关的现有、记录和预定义 AD FS 部署目标，并为您的情况开发工作解决方案。  
  
以前版本的 AD FS 最常部署为实现以下目的：  
  
-   使用基于 web\-的 SSO 体验为你的员工或客户提供企业内基于\-的应用程序的声明。  
  
-   为你的员工或客户提供基于 web\-的 SSO 体验，以访问任何联合伙伴组织中的资源。  
  
-   当远程访问内部托管的网站或服务时，为你的员工或客户提供基于 Web\-的 SSO 体验。  
  
-   在访问云中的资源或服务时，为你的员工或客户提供基于 web\-的 SSO 体验。  
  
除此之外，Windows Server 中 AD FS&reg; 2012 R2 添加了可帮助你实现以下目的的功能：  
  
-   SSO 设备工作区加入和无缝第二重身份验证。 这使组织可以允许从用户的个人设备进行访问，并在提供此访问时管理风险。  
  
-   使用多\-因素访问控制管理风险。 AD FS 提供控制谁能够访问什么应用程序的丰富授权级别。 这可以基于用户属性 \(UPN、电子邮件、安全组成员身份、身份验证强度等）\)、设备属性 \(设备是否已加入工作区\) 或请求属性 \(网络位置、IP 地址或用户代理\)。  
  
-   利用针对敏感应用程序的附加多\-因素身份验证管理风险。 AD FS 允许你控制策略，以在全局或每个应用程序的基础上需要多个\-因素身份验证。 此外，AD FS 为任何多\-因素供应商提供扩展点，以便为最终用户提供安全且无缝的多重\-因素体验。  
  
-   提供身份验证和授权功能，以便从 Web 应用程序代理保护的 extranet 访问 web 资源。  
  
总而言之，可以部署 Windows Server 2012 R2 中的 AD FS，以在你的组织中实现以下目标：  
  
### <a name="enable-your-users-to-access-resources-on-their-personal-devices-from-anywhere"></a>使用户能够从任何位置访问其个人设备上的资源  
  
-   工作区加入使用户能够将个人设备加入企业 Active Directory，因此，他们在从这些设备访问企业资源时能够获得访问权限和无缝体验。  
  
-   对企业网络内由 Web 应用程序代理保护并从 internet 进行访问的资源进行\-身份验证。  
  
-   密码更改使用户能够在密码过期时从任何加入工作区的设备更改密码，以便他们能够继续访问资源。  
  
### <a name="enhance-your-access-control-risk-management-tools"></a>增强访问控制风险管理工具  
在每个 IT 组织中，管理风险都是管理和合规的一个重要方面。 Windows Server&reg; 2012 R2 的 AD FS 中有大量的访问控制风险管理增强功能，其中包括：  
  
-   基于网络位置的灵活控制，可管理用户如何进行身份验证以访问受保护的应用程序 AD FS\-。  
  
-   灵活的策略，可确定用户是否需要基于用户的数据、设备数据和网络位置执行多重\-因素身份验证。  
  
-   每个\-应用程序控制，可忽略 SSO 并强制用户在每次访问敏感应用程序时提供凭据。  
  
-   基于用户数据、设备数据或网络位置，按\-应用程序访问策略灵活。  
  
-   AD FS Extranet 锁定，使管理员能够保护 Active Directory 帐户免受来自 Internet 的暴力攻击。  
  
-   访问吊销，可用于 Active Directory 中禁用或删除的任何加入工作区的设备。  
  
### <a name="use-ad-fs-to-enhance-the-sign-in-experience"></a>使用 AD FS 增强签名\-体验  
下面是 Windows Server&reg; 2012 R2 中的新 AD FS 功能，它使管理员能够自定义和增强签署\-体验：  
  
-   统一自定义 AD FS 服务，进行一次更改后，更改随后会自动传播到给定场中的剩余 AD FS 联合服务器。  
  
-   已更新的页面中的签名\-会自动搜索到不同的外形规格。  
  
-   支持自动回退到基于表单\-的身份验证，适用于未加入公司域但仍用于从企业网络内部 \(intranet\)生成访问请求的设备。  
  
-   简单控制，可自定义公司徽标、插图图像、IT 支持标准链接、主页、隐私等。  
  
-   在页面的符号\-中自定义说明消息。  
  
-   自定义 Web 主题。  
  
-   主领域发现 \(HRD\) 基于用户的组织后缀，以便为公司伙伴提供增强的隐私。  
  
-   HRD 按每个\-应用程序进行筛选，根据应用程序自动选取一个领域。  
  
-   一\-单击 "错误报告"，以便更轻松地进行故障排除。  
  
-   可自定义错误消息。  
  
-   多个身份验证提供程序可用时，提供用户身份验证选择。  
  
## <a name="see-also"></a>另请参阅  
[Windows Server 2012 R2 中的 AD FS 设计指南](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)  
  

