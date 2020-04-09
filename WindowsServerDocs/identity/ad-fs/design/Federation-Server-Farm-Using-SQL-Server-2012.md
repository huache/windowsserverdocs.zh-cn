---
ms.assetid: 6618b3ce-0e94-4009-b887-d8e05453358b
title: 使用 SQL Server 的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 862cbc74833e2d4e9f385ba961b58a1f703e6611
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853130"
---
# <a name="federation-server-farm-using-sql-server"></a>使用 SQL Server 的联合服务器场

Active Directory 联合身份验证服务 \(AD FS\) 的这一拓扑与使用 Windows 内部数据库 \(WID\) 部署拓扑的联合服务器场不同，因为它不会将数据复制到场中的每个联合服务器。 相反，场中的所有联合服务器都可以读取数据并将其写入到存储在运行 Microsoft SQL Server 位于企业网络中的服务器上的公共数据库中。  
  
## <a name="deployment-considerations"></a>部署注意事项  
本部分介绍有关与此部署拓扑相关的目标受众、权益和限制的各种注意事项。  
  
### <a name="who-should-use-this-topology"></a>谁应该使用此拓扑？  
  
-   具有超过100个信任关系的大型组织，需要为其内部用户和外部用户提供对 \(SSO 的单一登录\-\) 对联合应用程序或服务的访问权限  
  
-   已使用 SQL Server 并且想要利用其现有工具和专业知识的组织  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>使用此拓扑的好处是什么？  
  
-   支持 \(超过 100\) 的更多信任关系  
  
-   支持令牌重播检测 \(安全功能\) 和项目解析 \(安全断言标记语言 \(SAML\) 2.0 协议的一部分\)  
  
-   支持 SQL Server 的全部好处，如数据库镜像、故障转移群集、报告和管理工具  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>使用此拓扑的限制是什么？  
  
-   默认情况下，此拓扑不提供数据库冗余。 尽管具有 WID 拓扑的联合服务器场会自动复制场中每个联合服务器上的 WID 数据库，但带有 SQL Server 拓扑的联合服务器场只包含数据库的一个副本  
  
> [!NOTE]  
> SQL Server 支持多种不同的数据和应用程序冗余选项，包括故障转移群集、数据库镜像和多种不同类型的 SQL Server 复制。  
  
Microsoft 信息技术 \(IT\) 部门使用高\-安全 SQL Server 数据库镜像 \(同步\) 模式和故障转移群集，为\-实例提供高 SQL Server 可用性支持。 SQL Server 事务性 \(对等\-到\-对等\) 和合并复制尚未由 Microsoft 的 AD FS 产品团队测试。 有关 SQL Server 的详细信息，请参阅[高可用性解决方案概述](https://go.microsoft.com/fwlink/?LinkId=179853)或[选择适当的复制类型](https://go.microsoft.com/fwlink/?LinkId=214648)。  
  
### <a name="supported-sql-server-versions"></a>支持的 SQL Server 版本  
随 Windows Server 2012 一起安装 AD FS 支持以下 SQL server 版本：  
  
-   SQL Server 2008 \/ R2  
  
-   SQL 2012 Server  
  
## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议  
与带有 WID 拓扑的联合服务器场类似，场中的所有联合服务器都配置为使用一个群集域名系统 \(DNS\) 名称 \(表示联合身份验证服务名称\)，另一个群集 IP 地址作为网络负载平衡 \(NLB\) 群集配置的一部分。 这有助于 NLB 主机将客户端请求分配给各个联合服务器。 联合服务器代理可用于将客户端请求代理到联合服务器场。  
  
下图显示了虚构的 Contoso 制药公司如何在企业网络中部署具有 SQL Server 拓扑的联合服务器场。 它还显示了该公司如何配置具有对 DNS 服务器的访问权限的外围网络，另一个 NLB 主机使用同一群集 DNS 名称 \(在企业网络 NLB 群集上使用的 fs.contoso.com\)，以及两个联合服务器代理 \(fsp1 和 fsp2\)。  
  
![使用 SQL 的服务器场](media/FarmSQLProxies.gif)  
  
有关如何配置网络环境以用于联合服务器或联合服务器代理的详细信息，请参阅联合服务器的[名称解析要求](Name-Resolution-Requirements-for-Federation-Servers.md)或[联合服务器代理的名称解析要求](Name-Resolution-Requirements-for-Federation-Server-Proxies.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
