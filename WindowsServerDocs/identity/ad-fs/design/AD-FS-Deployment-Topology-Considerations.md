---
ms.assetid: 4ef052f0-61a9-4912-b780-5c96187c850f
title: AD FS 部署拓扑注意事项
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 42db104691bce75c37adf19eb97abba3bf579cf8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855870"
---
# <a name="ad-fs-deployment-topology-considerations"></a>AD FS 部署拓扑注意事项

本主题介绍一些重要的注意事项，这些注意事项有助于您规划和设计在生产环境中使用的 Active Directory 联合身份验证服务 \(AD FS\) 部署拓扑。 本主题是检查和评估会影响在部署 AD FS 后可使用哪些功能的注意事项的起点。 例如，根据选择存储 AD FS 配置数据库的数据库类型，将最终确定是否可以实现需要 SQL Server \(SAML\) 功能的某些安全断言标记语言。  

## <a name="determining-which-type-of-ad-fs-configuration-database-to-use"></a>确定要使用哪种类型的 AD FS 配置数据库  
AD FS 使用数据库来存储配置和（在某些情况下）与联合身份验证服务相关的事务数据。 您可以使用 AD FS 软件在 Windows 内部数据库中选择生成的\-\(WID\) 或 Microsoft SQL Server 2005 或更高版本，以便将数据存储在联合身份验证服务中。  

大多数情况下，这两个数据库类型是相对等效的。 但是，在开始阅读有关可用于 AD FS 的各种部署拓扑的详细信息之前，有一些不同之处需要注意。 下表描述了 WID 数据库和 SQL Server 数据库之间受支持的功能之间的差异。  

AD FS 功能  

|功能|WID 支持吗？|SQL Server 支持吗？|有关此功能的详细信息|  
|-----------|---------------------|----------------------------|---------------------------------------|  
|联合服务器场部署|是，每个场限制为30个联合服务器|可以。 对可以在单个服务器场中部署的联合服务器数目没有强制限制|[确定 AD FS 部署拓扑](Determine-Your-AD-FS-Deployment-Topology.md)|  
|SAML 项目解析**说明：** Microsoft Online Services、Microsoft Office 365、Microsoft Exchange 或 Microsoft Office SharePoint 方案不需要此功能。|是|是|[AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)<p>[AD FS 安全规划和部署的最佳做法](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)|  
|SAML\/WS\-联合身份验证令牌重放检测|是|是|[AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)<p>[AD FS 安全规划和部署的最佳做法](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)|  

数据库功能  

|功能|WID 支持吗？|SQL Server 支持吗？|有关此功能的详细信息|  
|-----------|---------------------|----------------------------|---------------------------------------|  
|使用 "拉" 复制的基本数据库冗余，其中的一个或多个服务器承载读取\-仅数据库请求的副本在承载数据库的\/读写副本的源服务器上所做的更改|是|是|[AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)|  
|使用高\-可用性解决方案（例如，仅在数据库层上的故障转移群集或镜像 \(提供数据库冗余\)**注意：** 所有 AD FS 部署拓扑都支持 AD FS 服务层的群集。|是|是|[AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)<p>[高可用性解决方案概述](https://go.microsoft.com/fwlink/?LinkId=179853)|  

### <a name="sql-server-considerations"></a>SQL Server 注意事项  
如果选择 SQL Server 作为 AD FS 部署的配置数据库，应考虑以下部署事实。  

-   **SAML 功能以及它们对数据库大小和增长的影响**。 当启用 SAML 项目解析或 SAML 令牌重放检测功能时，AD FS 会为颁发的每个 AD FS 令牌在 SQL Server 配置数据库中存储信息。 此活动导致的 SQL Server 数据库的增长不会被视为重要，它取决于已配置的令牌重播保留期。 每个项目记录的大小大约为 30 kb \(KB\)。  

-   **部署所需的服务器数目**。 你需要将至少一个额外的服务器 \(添加到部署 AD FS 基础结构的服务器总数，\) 该服务器将充当 SQL Server 实例的专用主机。 如果你计划使用故障转移群集或镜像为 SQL Server 配置数据库提供容错和可伸缩性，则至少需要两个 SQL server。  

### <a name="how-the-configuration-database-type-you-select-may-impact-hardware-resources"></a>你选择的配置数据库类型可能会影响硬件资源的方式  
对使用 WID 部署在场中的联合服务器上的硬件资源的影响，而不是在使用 SQL Server 数据库的场中部署的联合服务器。 但是，请务必注意，当你为场使用 WID 时，该场中的每个联合服务器必须存储、管理和维护其 AD FS 配置数据库的本地副本的复制更改，同时还会继续提供联合身份验证服务所需的正常操作。  

比较而言，在使用 SQL Server 数据库的场中部署的联合服务器不一定包含 AD FS 配置数据库的本地实例。 因此，它们可能会对硬件资源提出略少的要求。  

## <a name="verifying-that-your-production-environment-can-support-an-ad-fs-deployment"></a>验证你的生产环境是否可以支持 AD FS 部署  
除了你将部署的联合服务器，根据现有生产环境的设置方式，可能还需要以下其他服务器提供必要的基础结构，以支持新的 AD FS 部署：  

-   Active Directory 域控制器  

-   证书颁发机构 \(CA\)  

-   承载联合元数据的 Web 服务器  

-   网络负载平衡 \(NLB\)  

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
