---
title: 使用 AlwaysOn 可用性组设置 AD FS 部署
author: billmath
ms.author: billmath
manager: daveba
ms.date: 01/20/2020
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ddec398be56aba6d354b1863a98c8d641831415c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816090"
---
# <a name="setting-up-an-ad-fs-deployment-with-alwayson-availability-groups"></a>使用 AlwaysOn 可用性组设置 AD FS 部署
高度可用的异地分布式拓扑提供：
* 消除单点故障：借助故障转移功能，即使在地球的某个数据中心出现故障的情况下，也可以实现高度可用的 ADFS 基础结构。
* 提高性能：可以使用建议的部署来提供高性能 ADFS 基础结构

可以为高可用性异地分布式方案配置 AD FS。
以下指南将逐步概述 SQL Always on 可用性组的 AD FS，并提供部署注意事项和指南。

## <a name="overview---alwayson-availability-groups"></a>概述-AlwaysOn 可用性组

有关 AlwaysOn 可用性组的详细信息，请参阅[AlwaysOn 可用性组概述（SQL Server）](https://technet.microsoft.com/library/ff877884.aspx)

从 AD FS SQL Server 场的节点的角度来看，AlwaysOn 可用性组将单个 SQL Server 实例替换为策略/项目数据库。  可用性组侦听器是客户端（AD FS security token service）用于连接到 SQL 的内容。
下图显示了具有 AlwaysOn 可用性组的 AD FS SQL Server 场。

![使用 SQL 的服务器场](media/ad-fs-always-on/SQLoverview.png)

Always On 可用性组（AG）是一个或多个一起故障转移的用户数据库。 可用性组包含一个主可用性副本和一到四个辅助副本，这些副本通过 SQL Server 用于数据保护的基于日志的数据移动来维护，无需共享存储。 每个副本由 WSFC 的不同节点上 SQL Server 的实例承载。 可用性组和相应的虚拟网络名称注册为 WSFC 群集中的资源。

主副本节点上的可用性组侦听器响应连接到虚拟网络名称的传入客户端请求，并基于连接字符串中的属性将每个请求重定向到相应的 SQL Server 实例。
在发生故障转移时，可以利用 WSFC 重新配置另一个 SQL Server 实例上的辅助副本，使其成为可用性组的主副本，而不是将共享物理资源的所有权转移到另一个节点。 然后，将可用性组的虚拟网络名称资源转移到该实例。
在任意给定时刻，只有单个 SQL Server 实例可以承载可用性组数据库的主副本，所有关联的辅助副本都必须驻留在单独的实例上，并且每个实例必须驻留在单独的物理节点上。

> [!NOTE] 
> 如果计算机正在 Azure 上运行，请设置 Azure 虚拟机以使侦听器配置能够与 AlwaysOn 可用性组通信。 有关详细信息，请查看[虚拟机： SQL Always On 侦听器](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener)。

有关 AlwaysOn 可用性组的详细概述，请参阅[Always On 可用性组概述（SQL Server）](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server?view=sql-server-ver15)。

> [!NOTE] 
> 如果组织需要跨多个数据中心进行故障转移，则建议在每个数据中心创建一个项目数据库，并启用后台缓存，以便在请求处理过程中减少延迟。 按照说明进行操作以[优化 SQL，并减少延迟](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/adfs-sql-latency)。

## <a name="deployment-guidance"></a>部署指南

1. <b>为 AD FS 部署的目标考虑正确的数据库。</b>AD FS 使用数据库来存储配置以及与联合身份验证服务相关的事务数据。 您可以使用 AD FS 软件选择内置 Windows 内部数据库（WID）或 Microsoft SQL Server 2008 或更高版本，以便将数据存储在联合身份验证服务中。
下表描述了 WID 和 SQL 数据库的支持功能之间的差异。


| 类别      | 功能       | 受 WID 支持  | 支持 SQL |
| ------------------ |:-------------:| :---:|:---: |
| AD FS 功能     | 联合服务器场部署 | 是  | 是 |
| AD FS 功能     | SAML 项目解析。 注意：对于 SAML 应用程序而言，这种情况并不常见     |   是 | 是  |
| AD FS 功能 | SAML/WS 联合身份验证令牌重放检测。 注意：仅当 AD FS 从外部 Idp 接收令牌时才是必需的。 如果 AD FS 不是 IDP，则不需要执行此操作。      |    是  | 是 |
| 数据库功能     |   使用 "拉" 复制的基本数据库冗余，其中一个或多个承载数据库的只读副本的服务器请求在源服务器上所做的更改数据库的读/写副本    |   是 | 是  |
| 数据库功能 | 使用高可用性解决方案的数据库冗余，如群集或镜像（在数据库层）      |    是  | 是 |

如果你是具有超过100个信任关系的大型组织，需要为其内部用户和外部用户提供对联合应用程序或服务的单一登录访问，则建议使用 SQL 选项。

如果你的组织具有100或更低的已配置信任关系，则 WID 将提供数据和联合身份验证服务冗余（其中，每个联合服务器将更改复制到相同场中的其他联合服务器）。 WID 不支持令牌重播检测或项目解析，并且限制为30个联合服务器。
有关规划部署的详细信息，请访问[此处](https://docs.microsoft.com/windows-server/identity/ad-fs/design/planning-your-deployment)。

## <a name="sql-server-high-availability-solutions"></a>SQL Server 高可用性解决方案
如果使用 SQL Server 作为 AD FS 配置数据库，则可以使用 SQL Server 复制为 AD FS 场设置异地冗余。 异地冗余在两个地理位置较远的站点之间复制数据，以便应用程序可以从一个站点切换到另一个站点。 这样一来，如果一个站点发生故障，你仍可以在第二个站点上提供所有配置数据。 
如果 SQL 是用于部署目标的适当数据库，请继续学习本部署指南。

本指南将指导你完成以下工作
* 部署 AD FS
* 将 AD FS 配置为使用 AlwaysOn 可用性组
* 安装故障转移群集角色
* 运行群集验证测试
* 启用 Always On 可用性组
* 备份 AD FS 数据库
* 创建 AlwaysOn 可用性组
* 在第二个节点上添加数据库
* 将可用性副本联接到可用性组
* 更新 SQL 连接字符串

## <a name="deploy-ad-fs"></a>部署 AD FS

> [!NOTE] 
> 如果计算机正在 Azure 上运行，则必须以特定方式配置虚拟机，以允许侦听器与 Always On 可用性组通信。 有关配置的详细信息，请查看[在 Azure 上为可用性组配置负载均衡器 SQL Server vm](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener)


本部署指南将显示两个节点场，其中包含两个 SQL server 作为示例。
若要部署 AD FS 请按照下面的初始链接安装 AD FS 的角色服务。 若要为 AoA 组配置，还需要为角色执行其他步骤。
-   [将计算机加入域](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/join-a-computer-to-a-domain)
-   [为 AD FS 注册 SSL 证书](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/enroll-an-ssl-certificate-for-ad-fs)
-   [安装 AD FS 角色服务](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/install-the-ad-fs-role-service)


## <a name="configuring-ad-fs-to-use-an-alwayson-availability-group"></a>将 AD FS 配置为使用 AlwaysOn 可用性组

使用 AlwaysOn 可用性组配置 AD FS 场需要对 AD FS 部署过程做少许修改。 确保每个服务器实例运行相同版本的 SQL。 若要查看 Always On 可用性组的先决条件、限制和建议的完整列表，请参阅[此处](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability?view=sql-server-2017#PrerequisitesForDbs)。

1.  必须先创建要备份的数据库，然后才能配置 AlwaysOn 可用性组。  AD FS 在新 AD FS SQL Server 场的第一个联合身份验证服务节点的设置和初始配置过程中创建其数据库。  使用 SQL server 指定现有场的数据库主机名。 作为 AD FS 配置的一部分，你必须指定 SQL 连接字符串，因此必须将第一个 AD FS 场配置为直接连接到 SQL 实例（这只是暂时性的）。 有关配置 AD FS 场的特定指南，包括使用 SQL server 连接字符串配置 AD FS 场节点，请参阅[配置联合服务器](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/configure-a-federation-server)。

![指定场](media/ad-fs-always-on/deploymentSpecifyFarm.png)

2.  使用 SSMS 验证与数据库的连接，然后连接到目标数据库主机名。 如果将另一个节点添加到联合服务器场，请连接到目标数据库。
3.  指定 AD FS 场的 SSL 证书。

![指定 ssl 证书](media/ad-fs-always-on/deploymentSpecifySSL.png)

4.  将场连接到服务帐户或 gMSA。

![指定服务帐户](media/ad-fs-always-on/deploymentSpecifyServiceAccount.png)

5.  完成 AD FS 场配置和安装。

> [!NOTE] 
> 若要安装 Always On 可用性组，必须在域帐户下运行 SQL Server。 默认情况下，它作为本地系统运行。

## <a name="install-the-failover-clustering-role"></a>安装故障转移群集角色
Windows Server 故障转移群集角色提供了有关 Windows Server 故障转移群集的详细信息。
1.  启动服务器管理器。
2.  在 "管理" 菜单上，选择 "添加角色和功能"。
3.  在 "开始之前" 页上，选择 "下一步"。
4.  在 "选择安装类型" 页上，选择 "基于角色或基于功能的安装"，然后选择 "下一步"。
5.  在 "选择目标服务器" 页上，选择要安装功能的 SQL server，然后选择 "下一步"。

![目标服务器](media/ad-fs-always-on/clusteringDestinationServer.png)

6.  在 "选择服务器角色" 页上，选择 "下一步"。
7.  在“选择功能”页面上，选中“故障转移群集”复选框。

![选择群集功能](media/ad-fs-always-on/clusteringFeature.png)

8.  在 "确认安装选择" 页上，选择 "安装"。
无需为故障转移群集功能重新启动服务器。
9.  安装完成后，选择 "关闭"。
10. 在你想要添加为故障转移群集节点的每个服务器上重复此过程。

## <a name="run-cluster-validation-tests"></a>运行群集验证测试
1.  在已从远程服务器管理工具安装了故障转移群集管理工具的计算机上，或在安装了故障转移群集功能的服务器上，启动故障转移群集管理器。 若要在服务器上执行此操作，请启动服务器管理器，然后在 "工具" 菜单上，选择 "故障转移群集管理器"。
2.  在故障转移群集管理器窗格中的 "管理" 下，选择 "验证配置"。
3.  在 "开始之前" 页上，选择 "下一步"。
4.  在 "选择服务器或群集" 页上的 "输入名称" 框中，输入你计划添加为故障转移群集节点的服务器的 NetBIOS 名称或完全限定的域名，然后选择 "添加"。 为要添加的每台服务器重复此步骤。 若要同时添加多台服务器，请用逗号或分号分隔这些名称。 例如，采用格式 server1.contoso.com, server2.contoso.com 输入名称。 完成后，选择 "下一步"。

![选择服务器图片](media/ad-fs-always-on/clusterValidationServers.png)

5. 在 "测试选项" 页上，选择 "运行所有测试（推荐）"，然后选择 "下一步"。
6. 在 "确认" 页上，选择 "下一步"。
验证页面显示运行测试的状态。
7. 在“摘要”页面上，执行以下任一操作：
- 如果结果指示测试已成功完成且配置适用于群集，并且你想要立即创建群集，请确保选中 "使用已验证的节点创建群集" 复选框，然后选择 "完成"。 然后，继续执行[创建故障转移群集过程](https://docs.microsoft.com/windows-server/failover-clustering/create-failover-cluster#create-the-failover-cluster)的步骤4。

![验证配置图片](media/ad-fs-always-on/clusterValidationResults.png)

-   如果结果指示出现警告或失败，请选择 "查看报告" 以查看详细信息并确定必须更正的问题。 请注意，特定验证测试的警告指示可以支持故障转移群集的这个方面，但是可能不符合推荐的最佳做法。

> [!NOTE]
> 如果你收到“验证存储空间永久保留”测试的警告，请参阅博客文章 [Windows 故障转移群集验证警告指示你的磁盘不支持存储空间的永久保留](https://blogs.msdn.microsoft.com/clustering/2013/05/24/validate-storage-spaces-persistent-reservation-test-results-with-warning/) 以获取详细信息。
> 有关硬件验证测试的详细信息，请参阅[验证故障转移群集的硬件](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134244(v%3dws.11))。

## <a name="create-the-failover-cluster"></a>创建故障转移群集

若要完成此步骤，确保登录的用户帐户满足本主题的[验证先决条件](https://docs.microsoft.com/windows-server/failover-clustering/create-failover-cluster#verify-the-prerequisites)部分中概述的要求。
1.  启动服务器管理器。
2.  在 "工具" 菜单中，选择故障转移群集管理器。
3.  在故障转移群集管理器窗格中的 "管理" 下，选择 "创建群集"。
将会打开“创建群集向导”。
4.  在 "开始之前" 页上，选择 "下一步"。
5.  如果显示 "选择服务器" 页，则在 "输入名称" 框中，输入你计划添加为故障转移群集节点的服务器的 NetBIOS 名称或完全限定的域名，然后选择 "添加"。 为要添加的每台服务器重复此步骤。 若要同时添加多台服务器，请用逗号或分号分隔这些名称。 例如，采用格式 server1.contoso.com; server2.contoso.com 输入名称。 完成后，选择 "下一步"。

![创建群集并选择服务器](media/ad-fs-always-on/createClusterServers.png)

> [!NOTE]
> 如果在[配置验证过程](https://docs.microsoft.com/windows-server/failover-clustering/create-failover-cluster#validate-the-configuration)中运行验证后立即选择创建群集，将不会看到 "选择服务器" 页。 已验证的节点会自动添加到创建群集向导中，以便你无需再次输入它们。

6.  如果你提前跳过验证，则会出现“验证警告”页面。 我们强烈建议你运行群集验证。 Microsoft 仅支持通过所有验证测试的群集。 若要运行验证测试，请选择 "是"，然后选择 "下一步"。 完成验证配置向导，如[验证配置](https://docs.microsoft.com/windows-server/failover-clustering/create-failover-cluster#validate-the-configuration)中所述。
7.  在“用于管理群集的访问点”页面上，执行以下操作：
-   在“群集名称”框中，输入你要用于管理群集的名称。 在执行此操作之前，请查看以下信息：
 -  在群集创建期间，此名称在 AD DS 中注册为群集计算机对象（也称为群集名称对象或 CNO）。 如果为群集指定 NetBIOS 名称，则在群集节点的计算机对象所在的同一位置中创建 CNO。 这可以是默认的计算机容器或 OU。
 -  若要为 CNO 指定不同的位置，你可以在“群集名称”框中输入 OU 的可分辨名称。 例如： CN = ClusterName，OU = 集群，DC = Contoso，DC = com。
 -  如果域管理员在与群集节点所在的不同 OU 中预留了 CNO，则指定域管理员提供的可分辨名称。
- 如果该服务器没有配置为使用 DHCP 的网络适配器，则必须为该故障转移群集配置一个或多个静态 IP 地址。 选中你想要用于群集管理的每个网络旁边的复选框。 选择所选网络旁边的 "地址" 字段，然后输入要分配给群集的 IP 地址。 此 IP 地址（或多个地址）将与域名系统 (DNS) 中的群集名称相关联。
- 完成后，选择 "下一步"。

8.  在“确认”页面上，查看这些设置。 默认情况下，选中“将所有符合条件的存储添加到群集”复选框。 如果你想要执行以下任一操作，请清除此复选框：
-   你想要稍后配置存储。
-   你打算通过故障转移群集管理器或通过故障转移群集 Windows PowerShell cmdlet 创建群集存储空间，并且尚未在文件和存储服务中创建存储空间。 有关详细信息，请参阅[部署群集存储空间](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj822937(v%3dws.11))。
9.  选择 "下一步" 以创建故障转移群集。
10. 在“摘要”页面上，确认已成功创建故障转移群集。 如果出现任何警告或错误，请查看摘要输出或选择 "查看报告" 以查看完整报告。 选择“完成”。
11. 若要确认已创建群集，请验证该群集名称在导航树中的“故障转移群集管理器”下列出。 你可以展开群集名称，然后选择 "节点"、"存储" 或 "网络" 下的项以查看关联的资源。
请注意，在 DNS 中成功复制群集名称可能需要花一些时间。 成功进行 DNS 注册和复制之后，如果选择 "服务器管理器中的" 所有服务器 "，则群集名称应作为可管理性状态为" 联机 "的服务器列出。

![创建群集完成](media/ad-fs-always-on/createClusterComplete.png)

## <a name="enable-always-on-availability-groups-with-sql-server-configuration-manager"></a>使用 SQL Server 配置管理器启用 Always on 可用性组

1.  连接到承载要在其中启用 Always On 可用性组的 SQL Server 实例的 Windows Server 故障转移群集（WSFC）节点。
2.  在 "开始" 菜单上，依次指向 "所有程序"、"Microsoft SQL Server" 和 "配置工具"，然后单击 "SQL Server 配置管理器"。
3.  在 SQL Server 配置管理器中，单击 "SQL Server 服务"，右键单击 SQL Server （<instance name>），其中 <instance name> 是要为其启用 Always On 可用性组的本地服务器实例的名称，然后单击 "属性"。
4.  选择 "Always On 高可用性" 选项卡。
5.  验证“Windows 故障转移群集名称”字段包含本地故障转移群集的名称。 如果此字段为空，则此服务器实例当前不支持 Always On 可用性组。 本地计算机不是群集节点、WSFC 群集已关闭或此版本的 SQL Server 不支持 Always On 可用性组。
6.  选中 "启用 Always On 可用性组" 复选框，然后单击 "确定"。
SQL Server 配置管理器会保存您的更改。 然后，必须手动重新启动 SQL Server 服务。 这使您可以选择最适合您的业务要求的重新启动时间。 当 SQL Server 服务重新启动时，将启用 Always On，并且 IsHadrEnabled 服务器属性将设置为1。

![启用 AoA](media/ad-fs-always-on/enableAoAGroup.png)

## <a name="back-up-ad-fs-databases"></a>备份 AD FS 数据库
备份具有完整事务日志的 AD FS 配置和项目数据库。 将备份置于所选的目标位置。
备份 ADFS 项目和配置数据库。
- 任务 > 备份 > 完整 > 添加到备份文件 > "确定" 创建

![备份服务器](media/ad-fs-always-on/backUpADFS.png)

## <a name="create-new-availability-group"></a>创建新的可用性组

1.  在对象资源管理器中，连接到承载主副本的服务器实例。
2.  展开 "Always On 高可用性" 节点和 "可用性组" 节点。
3.  若要启动新建可用性组向导，请选择“新建可用性组向导”命令。
4.  首次运行该向导时，“简介”页将出现。 若要在将来跳过此页，可单击“不再显示此页”。 在阅读了此页后，单击“下一步”。
5.  在 "指定可用性组选项" 页上，在 "可用性组名称" 字段中输入新可用性组的名称。 此名称必须是有效的 SQL Server 标识符，该标识符在群集和域中是唯一的。 可用性组名称的最大长度为128个字符。 e
6.  接下来，指定群集类型。 可能的群集类型取决于 SQL Server 版本和操作系统。 选择 "WSFC"、"外部" 或 "无"。 有关详细信息，请参阅 "[指定可用性组名称](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/specify-availability-group-name-page?view=sql-server-ver15)" 页

![名称 AoA 组和群集](media/ad-fs-always-on/createAoAName.png)

7.  在“选择数据库”页上，网格中列出所连接的服务器实例上有资格成为“可用性数据库”的用户数据库。 选择一个或多个列出的数据库以参与新的可用性组。 这些数据库最初将成为初始“主数据库”。
对于每个列出的数据库，“大小”列显示数据库大小（如果已知）。 "状态" 列指示给定的数据库是否符合可用性数据库的[先决条件](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability?view=sql-server-ver15)。 如果不满足先决条件，则简要的状态说明将指示数据库不合格的原因;例如，如果它不使用完整恢复模式。 有关详细信息，请单击状态说明。
如果数据库经过更改已经合格，请单击“刷新”以更新数据库网格。
如果数据库包含数据库主密钥，则请在“密码”列中输入数据库主密钥的密码。

![为 AoA 选择数据库](media/ad-fs-always-on/createAoASelectDb.png)

8. 在 "指定副本" 页上，为新的可用性组指定和配置一个或多个副本。 此页包含四个选项卡。 下表介绍了这些选项卡。 有关详细信息，请参阅 "[指定副本" 页（新建可用性组向导：添加副本向导）](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard?view=sql-server-ver15)主题。

| 选项卡      | 简要描述       |
| ------------------ |:-------------:|
| 副本     | 使用此选项卡可以指定将承载辅助副本的每个 SQL Server 实例。 请注意，您当前连接到的服务器实例必须承载主副本。 |
| 终结点     | 使用此选项卡可以验证任何现有数据库镜像终结点，并且如果此终结点在其服务帐户使用 Windows 身份验证的服务器实例上不存在，则自动创建终结点。|
| 备份首选项 | 使用此选项卡为可用性组指定您的备份首选项，并为各个可用性副本指定备份优先级。      |
| Listener     | 使用此选项卡可以创建可用性组侦听器。 默认情况下，该向导不创建侦听器。      |

![指定副本详细信息](media/ad-fs-always-on/createAoAchooseReplica.png)

9. 在“选择初始数据同步”页上，选择如何创建新的辅助数据库并将其联接到可用性组。 选择下列选项之一：
-   自动种子设定
 - SQL Server 会自动为该组中的每个数据库创建辅助副本。 自动种子设定要求数据和日志文件路径在参与组的每个 SQL Server 实例上都相同。 在 SQL Server 2016 （13. x）和更高版本上可用。 请参阅[自动初始化 Always On 可用性组](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group?view=sql-server-ver15)。
- 完整数据库和日志备份
 - 如果你的环境满足自动启动初始数据同步的要求，则选择此选项（有关详细信息，请参阅[本主题前面的先决条件、限制和建议）](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio?view=sql-server-ver15#Prerequisites)。
如果选择“完全”，则在创建可用性组后，向导会将每个主数据库及其事务日志备份到网络共享，并在每个承载辅助副本的服务器实例上还原备份。 然后，该向导将每个辅助数据库联接到该可用性组。
在“指定可由所有副本访问的共享网络位置”字段中，指定承载副本的所有服务器都具有读写访问权限的备份共享。 有关详细信息，请参阅本主题前面的先决条件。 在验证步骤中，向导将执行测试以确保所提供的网络位置有效，此测试将在名为 "BackupLocDb_" 的主副本上创建一个名为 "" 的数据库，后跟一个 Guid，然后对提供的网络位置执行备份，然后将其还原到辅助副本。 如果向导无法删除此数据库，则可以安全删除该数据库及其备份历史记录和备份文件。
- 仅联接
 - 如果已在将承载辅助副本的服务器实例上手动准备了辅助数据库，则可以选择此选项。 向导会将现有辅助数据库联接到可用性组。
- 跳过初始数据同步
 - 如果要使用自己的数据库和主数据库的日志备份，请选择此选项。 有关详细信息，请参阅[在 Always On 辅助数据库上启动数据移动（SQL Server）](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server?view=sql-server-ver15)。

![选择数据同步选项](media/ad-fs-always-on/createAoADataSync.png)

9.  “验证”页验证在此向导中指定的值是否满足新建可用性组向导的要求。 若要进行更改，请单击“上一页”以返回前面的向导页，更改一个或多个值。 单击“下一步”返回到“验证”页，然后单击“重新运行验证”。

10. 在“摘要”页上，查看您为新的可用性组进行的选择。 若要进行更改，请单击“上一步”以返回到相应页。 在进行更改后，单击“下一步”以返回到“摘要”页。

> [!NOTE] 
> 如果将承载新可用性副本的服务器实例的 SQL Server 服务帐户不作为登录名存在，则新建可用性组向导需要创建该登录名。 在“摘要”页上，该向导将显示要创建的登录名的信息。 如果单击“完成”，则该向导将为 SQL Server 服务帐户创建该登录名，并授予该登录名 CONNECT 权限。
> 如果您满意所做的选择，可以选择单击“脚本”以创建向导将执行的步骤的脚本。 然后，若要创建和配置新的可用性组，请单击“完成”。

11. “进度”页将显示创建可用性组的各步骤（配置端点、创建可用性组和将辅助副本联接到该组）的进度。
12. 在这些步骤完成后，“结果”页将显示各步骤的结果。 如果所有这些步骤都成功，则会完全配置新的可用性组。 如果任何步骤导致错误，您可能需要手动完成配置或对失败的步骤使用向导。 有关给定错误的原因的信息，请单击“结果”列中关联的“错误”链接。
完成向导后，单击“关闭”以退出安装向导。

![验证完成](media/ad-fs-always-on/createAoAValidation.png)

## <a name="add-databases-on-secondary-node"></a>添加辅助节点上的数据库

1.  使用创建的备份文件通过辅助节点上的 UI 还原项目数据库。
通过 UI](media/ad-fs-always-on/restoreDB.png) ![还原

2. 在非恢复状态中还原数据库。
![还原和非恢复](media/ad-fs-always-on/restoreNonRecovery.png)

3. 重复还原配置数据库的过程。

## <a name="join-availability-replica-to-an-availability-group"></a>将可用性副本联接到可用性组

1.  在对象资源管理器中，连接到承载辅助副本的服务器实例，然后单击服务器名称以展开服务器树。
2.  展开 "Always On 高可用性" 节点和 "可用性组" 节点。
3.  选择您连接到的辅助副本的可用性组。
4.  右键单击辅助副本，然后单击“联接到可用性组”。
5.  这将打开“将副本联接到可用性组”对话框。
6.  若要将辅助副本联接到可用性组，请单击“确定”。

![联接辅助副本](media/ad-fs-always-on/jointoAoA.png)

## <a name="update-the-sql-connection-string"></a>更新 SQL 连接字符串
最后，使用 PowerShell 编辑 AD FS 属性，将 SQL 连接字符串更新为使用 AlwaysOn 可用性组侦听器的 DNS 地址。
在每个节点上运行配置数据库更改，并在所有 ADFS 节点上重新启动 ADFS 服务。 初始目录值根据场版本更改。

```
PS:\>$temp= Get-WmiObject -namespace root/ADFS -class SecurityTokenService
PS:\>$temp.ConfigurationdatabaseConnectionstring=”data source=<SQLCluster\SQLInstance>; initial catalog=adfsconfiguration;integrated security=true”
PS:\>$temp.put()
PS:\> Set-AdfsProperties –artifactdbconnection ”Data source=<SQLCluster\SQLInstance >;Initial Catalog=AdfsArtifactStore;Integrated Security=True”
```
