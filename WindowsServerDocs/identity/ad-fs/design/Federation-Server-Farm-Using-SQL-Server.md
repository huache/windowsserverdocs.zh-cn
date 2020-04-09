---
ms.assetid: e983d2ab-4153-41e7-b243-12cf7d71a552
title: 使用 SQL Server 的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: fd82edbcd2403416a08a4d707e5271ab2ced4b22
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853120"
---
# <a name="federation-server-farm-using-sql-server"></a>使用 SQL Server 的联合服务器场

Active Directory 联合身份验证服务 \(AD FS\) 的这一拓扑与使用 Windows 内部数据库 \(WID\) 部署拓扑的联合服务器场不同，因为它不会将数据复制到场中的每个联合服务器。 相反，场中的所有联合服务器都可以读取数据并将其写入到存储在运行 Microsoft SQL Server 位于企业网络中的服务器上的公共数据库中。  
  
> [!IMPORTANT]  
> 如果要创建 AD FS 场并使用 SQL Server 来存储配置数据，可以使用 SQL Server 2008 和更新版本，包括 SQL Server 2012 和 SQL Server 2014。  
  
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
Windows Server 2012 R2 中 AD FS 支持以下 SQL server 版本：  
  
-   SQL Server 2008 \/ R2  
  
-   SQL 2012 Server  
  
-   SQL Server 2014  
  
## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议  
与带有 WID 拓扑的联合服务器场类似，场中的所有联合服务器都配置为使用一个群集域名系统 \(DNS\) 名称 \(表示联合身份验证服务名称\)，另一个群集 IP 地址作为网络负载平衡 \(NLB\) 群集配置的一部分。 这有助于 NLB 主机将客户端请求分配给各个联合服务器。 联合服务器代理可用于将客户端请求代理到联合服务器场。  
  
下图显示了虚构的 Contoso 制药公司如何在企业网络中部署具有 SQL Server 拓扑的联合服务器场。 它还显示了该公司如何配置具有对 DNS 服务器的访问权限的外围网络，另一个 NLB 主机使用同一群集 DNS 名称 \(在企业网络 NLB 群集上使用的 fs.contoso.com\)，以及两个 web 应用程序代理 \(wap1 和 wap2\)。  
  
![使用 SQL 的服务器场](media/SQLFarmADFSBlue.gif)  
  
有关如何配置网络环境以用于联合服务器或 web 应用程序代理的详细信息，请参阅[AD FS 要求](AD-FS-Requirements.md)和[规划 Web 应用程序代理基础结构（WAP）](https://technet.microsoft.com/library/dn383648.aspx)中的 "名称解析要求" 部分。  
  
## <a name="high-availability-options-for-sql-server-farms"></a>SQL Server 场的高可用性选项  
在 Windows Server 2012 R2 中，AD FS 使用 SQL Server 在 AD FS 场中提供了两个新的选项来支持高可用性。  
  
-   支持 SQL Server AlwaysOn 可用性组  
  
-   支持使用 SQL Server 合并复制实现地理分布式高可用性  
  
本部分介绍其中的每个选项、它们分别解决的问题，以及确定要部署的选项的一些关键注意事项。  
  
> [!NOTE]  
> 使用 Windows 内部数据库的 AD FS 场 \(WID\) 提供对主联合服务器节点上的读取\/写入访问权限的基本数据冗余，并读取仅在辅助节点上的\-访问权限。  这可用于地理位置分散的本地或分散的拓扑。  
>   
> 使用 WID 时，请注意以下限制：  
>   
> -   如果有100个或更少的信赖方信任，则 WID 场的限制为30个联合服务器。  
> -   WID 场不支持令牌重播检测或项目解析 \(安全断言标记语言 \(SAML\) 协议\)的一部分。  
  
下表简要介绍了如何使用 WID 场。  
  
||||  
|-|-|-|  
||1 \- 100 RP 信任|超过 100 RP 信任|  
|1 \- 30 AD FS 节点|支持 WID|不支持使用 WID \- 需要 SQL|  
|超过30个 AD FS 节点|不支持使用 WID \- 需要 SQL|不支持使用 WID \- 需要 SQL|  
  
### <a name="alwayson-availability-groups"></a>AlwaysOn 可用性组  
**概述**  
  
AlwaysOn 可用性组是在 SQL Server 2012 中引入的，提供了一种新的方式来创建高可用性 SQL Server 实例。  AlwaysOn 可用性组合并了群集和数据库镜像的元素，以便在 SQL 实例层和数据库层上实现冗余和故障转移。  不同于以前的高可用性选项，AlwaysOn 可用性组不需要在数据库层\) 公用存储 \(或存储区域网络。  
  
可用性组包含一个主副本 \(一组读取\-写入主数据库\) 和一到四个可用性副本 \(一组对应的辅助数据库\)。  可用性组支持 \(主要副本\)的单个读取\-写入副本和一到四个读取\-唯一可用性副本。  每个可用性副本必须位于单个 Windows Server 故障转移群集的不同节点上 \(WSFC\) 群集。  有关 AlwaysOn 可用性组的详细信息，请参阅[AlwaysOn 可用性组 \(概述 SQL Server\)](https://technet.microsoft.com/library/ff877884.aspx)。  
  
从 AD FS SQL Server 场的节点的角度来看，AlwaysOn 可用性组将单个 SQL Server 实例替换为 \/ 项目数据库策略。  可用性组侦听器是客户端 \(AD FS security token service\) 用于连接到 SQL 的内容。  
  
下图显示了具有 AlwaysOn 可用性组的 AD FS SQL Server 场。  
  
![使用 SQL 的服务器场](media/alwaysonavailabilitygroups.jpg)  
  
> [!NOTE]  
> AlwaysOn 可用性组要求 SQL Server 实例驻留在 Windows Server 故障转移群集 \(WSFC\) 节点上。  
  
> [!NOTE]  
> 只有一个可用性副本可充当自动故障转移目标，另外三个副本将依赖于手动故障转移。  
  
**重要部署注意事项**  
  
如果你计划将 AlwaysOn 可用性组与 SQL Server 合并复制一起使用，请注意下面的 "使用 AD FS 与 SQL Server 合并复制有关的重要部署注意事项" 中所述的问题。  特别是，当包含作为复制订阅服务器的数据库的 AlwaysOn 可用性组发生故障转移时，复制订阅将失败。 要恢复复制，复制管理员必须手动重新配置订阅服务器。  请参阅复制订阅服务器上的特定问题的 SQL Server 说明，[并 AlwaysOn 可用性组 \(SQL Server\)](https://technet.microsoft.com/library/hh882436.aspx)和针对 AlwaysOn 可用性组的总体支持声明，其中复制选项为[复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组](https://technet.microsoft.com/library/hh403414.aspx)\(SQL Server\)。  
  
**将 AD FS 配置为使用 AlwaysOn 可用性组**  
  
使用 AlwaysOn 可用性组配置 AD FS 场需要对 AD FS 部署过程稍作修改：  
  
1.  必须先创建要备份的数据库，然后才能配置 AlwaysOn 可用性组。  AD FS 在新 AD FS SQL Server 场的第一个联合身份验证服务节点的设置和初始配置过程中创建其数据库。  作为 AD FS 配置的一部分，你必须指定 SQL 连接字符串，因此必须将第一个 AD FS 场节点配置为直接连接到 SQL 实例，\(这只是临时\)。   有关配置 AD FS 场的特定指南，包括使用 SQL server 连接字符串配置 AD FS 场节点，请参阅[配置联合服务器](../../ad-fs/deployment/Configure-a-Federation-Server.md)。  
  
2.  创建 AD FS 数据库后，请将其分配给 AlwaysOn 可用性组，并在[创建和配置可用性组 \(SQL Server\)](https://technet.microsoft.com/library/ff878265.aspx)时，使用 SQL Server 工具和过程创建公共 TCPIP 侦听器。  
  
3.  最后，使用 PowerShell 编辑 AD FS 属性，将 SQL 连接字符串更新为使用 AlwaysOn 可用性组侦听器的 DNS 地址。  
  
    用于更新 AD FS 配置数据库的 SQL 连接字符串的示例 PSH 命令：  
  
    ```  
    PS:\>$temp= Get-WmiObject -namespace root/ADFS -class SecurityTokenService  
    PS:\>$temp.ConfigurationdatabaseConnectionstring="data source=<SQLCluster\SQLInstance>; initial catalog=adfsconfiguration;integrated security=true"  
    PS:\>$temp.put()  
  
    ```  
  
4.  用于更新 AD FS 项目解析服务数据库的 SQL 连接字符串的示例 PSH 命令：  
  
    ```  
    PS:\> Set-AdfsProperties –artifactdbconnection "Data source=<SQLCluster\SQLInstance >;Initial Catalog=AdfsArtifactStore;Integrated Security=True"  
    ```  
  
### <a name="sql-server-merge-replication"></a>SQL Server 合并复制  
合并复制还在 SQL Server 2012 中引入，允许 AD FS 策略数据冗余，并具有以下特征：  
  
-   所有节点上的读取和写入功能 \(不只是主\)  
  
-   异步复制的数据量较小，以避免引入系统延迟  
  
下图显示了地理冗余 AD FS SQL Server 包含合并复制的服务器场，\(1 个发布服务器，2个订阅服务器\)：  
  
![使用 SQL 的服务器场](media/ADFSSQLGeoRedundancy3.png)  
  
**将 AD FS 与 SQL Server 合并复制结合使用的重要部署注意事项 \(上图中的说明编号\)**  
  
-   不支持将分发服务器数据库用于 AlwaysOn 可用性组或数据库镜像。  请参阅 SQL Server 支持语句中的 AlwaysOn 可用性组，复制选项[、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 \(SQL Server\)](https://technet.microsoft.com/library/hh403414.aspx)。  
  
-   包含作为复制订阅服务器的数据库的 AlwaysOn 可用性组发生故障转移时，复制订阅将失败。 要恢复复制，复制管理员必须手动重新配置订阅服务器。  请参阅复制订阅服务器上特定问题的 SQL Server 说明[，并 AlwaysOn 可用性组 \(SQL Server\)](https://technet.microsoft.com/library/hh882436.aspx)和针对 AlwaysOn 可用性组的总体支持声明，其中包含复制选项[复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组](https://technet.microsoft.com/library/hh403414.aspx)\(SQL Server\)。  
  
有关如何配置 AD FS 以使用 SQL Server 合并复制的更多详细说明，请参阅[使用 SQL Server 复制设置地理冗余](https://technet.microsoft.com/library/dn632406.aspx)。  
  
## <a name="see-also"></a>另请参阅  
[规划 AD FS 部署拓扑](Plan-Your-AD-FS-Deployment-Topology.md)  
[Windows Server 2012 R2 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)  
  

