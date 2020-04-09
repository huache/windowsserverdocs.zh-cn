---
ms.assetid: 8890ccc9-068d-4da2-bd51-8a2964173ff1
title: 使用 WID 和代理的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9c6dba880b80de43bb713d1b4495f0e03d56a695
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853090"
---
# <a name="federation-server-farm-using-wid-and-proxies"></a>使用 WID 和代理的联合服务器场

此 Active Directory 联合身份验证服务 \(AD FS\) 的部署拓扑与 Windows 内部数据库 \(WID\) 拓扑的联合服务器场相同，但它将联合服务器代理添加到外围网络以支持外部用户。 联合服务器代理将来自企业网络外部的客户端身份验证请求重定向到联合服务器场。  
  
## <a name="deployment-considerations"></a>部署注意事项  
本部分介绍有关与此部署拓扑相关的目标受众、权益和限制的各种注意事项。  
  
### <a name="who-should-use-this-topology"></a>谁应该使用此拓扑？  
  
-   具有100或更少配置信任关系的组织，需要同时为其内部用户和外部用户提供 \(登录到物理位置位于企业网络之外的计算机上\) 使用单一登录\-\(SSO\) 访问联合应用程序或服务  
  
-   需要为内部用户和外部用户提供对 Microsoft Office 365 的 SSO 访问的组织  
  
-   具有外部用户并且需要冗余、可缩放服务的小型组织  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>使用此拓扑的好处是什么？  
  
-   [使用 WID 拓扑为联合服务器场](Federation-Server-Farm-Using-WID-2012.md)列出的优点，以及为外部用户提供其他访问权限的好处  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>使用此拓扑的限制是什么？  
  
-   [使用 WID 拓扑为联合服务器场](Federation-Server-Farm-Using-WID-2012.md)列出的限制相同  
  
## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议  
若要部署此拓扑，除了添加两个联合服务器代理外，还必须确保你的外围网络还可以提供对域名系统 \(DNS\) 服务器和第二个网络负载平衡 \(NLB\) 主机的访问权限。 第二个 NLB 主机必须配置一个 NLB 群集，该群集使用 Internet\-可访问的群集 IP 地址，并且它必须与你在公司网络上配置的以前的 NLB 群集 \(fs.fabrikam.com\)相同。 还应为联合服务器代理配置 Internet\-可访问的 IP 地址。  
  
下图显示了以前介绍的包含 WID 拓扑的现有联合服务器场以及虚构的 Fabrikam，Inc. 公司如何提供对外围 DNS 服务器的访问，如何添加具有相同群集 DNS 名称 \(fs.fabrikam.com\)的第二个 NLB 主机，并将两个联合服务器代理 \(fsp1 和 fsp2\) 添加到外围网络。  
  
![使用 WID 的服务器场](media/FarmWIDProxies.gif)  
  
有关如何配置网络环境以用于联合服务器或联合服务器代理的详细信息，请参阅联合服务器的[名称解析要求](Name-Resolution-Requirements-for-Federation-Servers.md)或[联合服务器代理的名称解析要求](Name-Resolution-Requirements-for-Federation-Server-Proxies.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
