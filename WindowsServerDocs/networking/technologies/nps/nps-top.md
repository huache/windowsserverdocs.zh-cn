---
title: 网络策略服务器 (NPS)
description: 本主题概述了 Windows Server 2016 和 Windows Server 2019 中的网络策略服务器，并包括指向有关 NPS 的其他指南的链接。
manager: dougkim
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 9c7a67e0-0953-479c-8736-ccb356230bde
ms.author: lizross
author: eross-msft
ms.date: 06/20/2018
ms.openlocfilehash: b509bb14757fab6ebd32490d0146b2801bc8e9f1
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315628"
---
# <a name="network-policy-server-nps"></a>网络策略服务器 (NPS)

>适用于： Windows Server （半年频道）、Windows Server 2016、Windows Server 2019

你可以使用本主题来概述 Windows Server 2016 和 Windows Server 2019 中的网络策略服务器。 在 Windows Server 2016 和服务器2019中安装网络策略和访问服务（NPAS）功能时，将安装 NPS。

> [!NOTE]
> 除本主题外，还提供以下 NPS 文档。
> - [网络策略服务器最佳做法](nps-best-practices.md)
> - [与网络策略服务器入门](nps-getstart-top.md)
> - [规划网络策略服务器](nps-plan-top.md)
> - [部署网络策略服务器](nps-deploy.md)
> - [管理网络策略服务器](nps-manage-top.md)
> - Windows PowerShell for Windows Server 2016 和 Windows 10[中的网络策略服务器（NPS） cmdlet](https://technet.microsoft.com/library/jj872739.aspx)
> - Windows PowerShell for Windows Server 2012 R2 和 Windows 8.1[中的网络策略服务器（NPS） cmdlet](https://technet.microsoft.com/library/jj872739.aspx)
> - Windows PowerShell for Windows Server 2012 和 Windows 8[中的 NPS cmdlet](https://technet.microsoft.com/library/jj872739.aspx)

通过网络策略服务器 (NPS)，你可以针对连接请求身份验证和授权创建并实施组织级网络访问策略。

你还可以将 NPS 配置为远程身份验证拨入用户服务（RADIUS）代理，以将连接请求转发到远程 NPS 或其他 RADIUS 服务器，以便可以对连接请求进行负载平衡，并将其转发到正确的域进行身份验证和授权。

NPS 允许使用以下功能集中配置和管理网络访问身份验证、授权和记帐：

- **RADIUS 服务器**。 NPS 为无线、身份验证交换机、远程访问拨号和虚拟专用网络（VPN）连接执行集中式身份验证、授权和记帐。 将 NPS 用作 RADIUS 服务器时，可以将无线访问点和 VPN 服务器等网络访问服务器配置为 NPS 中的 RADIUS 客户端。 还可以配置 NPS 用于对连接请求进行授权的网络策略，并且可以配置 RADIUS 记帐，以便 NPS 将记帐信息记录到本地硬盘上或 Microsoft SQL Server 数据库中的日志文件。 有关详细信息，请参阅[RADIUS 服务器](#radius-server)。
- **RADIUS 代理**。 将 NPS 用作 RADIUS 代理时，可以配置连接请求策略，通知 NPS 要将哪些连接请求转发到其他 RADIUS 服务器，以及要将连接请求转发到哪些 RADIUS 服务器。 还可以配置 NPS，以转发将由远程 RADIUS 服务器组中的一台或多台计算机记录的记帐数据。 若要将 NPS 配置为 RADIUS 代理服务器，请参阅以下主题。 有关详细信息，请参阅[RADIUS 代理](#radius-proxy)。
    - [配置连接请求策略](nps-crp-configure.md)
- **RADIUS 记帐**。 你可以配置 NPS，以将事件记录到本地日志文件或 Microsoft SQL Server 的本地或远程实例。 有关详细信息，请参阅[NPS 日志记录](#nps-logging)。

> [!IMPORTANT]
> 网络访问保护 \(NAP\)、健康注册机构 \(HRA\)和主机凭据授权协议 \(在 Windows Server 2012 R2 中已弃用，并且在 Windows Server 2016 中不可用。\) 如果使用早于 Windows Server 2016 的操作系统进行 NAP 部署，则不能将 NAP 部署迁移到 Windows Server 2016。

可以将 NPS 配置为具有这些功能的任意组合。 例如，你可以将一个 NPS 配置为用于 VPN 连接的 RADIUS 服务器，并将另一个 NPS 配置为 RADIUS 代理，以便将某些连接请求转发到远程 RADIUS 服务器组的成员，以便在另一个域中进行身份验证和授权。

## <a name="windows-server-editions-and-nps"></a>Windows Server 版本和 NPS

NPS 提供不同的功能，具体取决于你安装的 Windows Server 的版本。

### <a name="windows-server-2016-or-windows-server-2019-standarddatacenter-edition"></a>Windows Server 2016 或 Windows Server 2019 Standard/Datacenter Edition

使用 Windows Server 2016 Standard 或 Datacenter 中的 NPS，可以配置无限数量的 RADIUS 客户端和远程 RADIUS 服务器组。 此外，可以通过指定 IP 地址范围来配置 RADIUS 客户端。

> [!NOTE]
> 使用服务器核心安装选项安装的系统上的 "WIndows 网络策略和访问服务" 功能不可用。

以下各节提供有关 NPS 的更详细信息，如 RADIUS 服务器和代理。

## <a name="radius-server-and-proxy"></a>RADIUS 服务器和代理

可以将 NPS 用作 RADIUS 服务器、RADIUS 代理或同时使用这两者。

### <a name="radius-server"></a>RADIUS 服务器

NPS 是 Internet 工程任务组在 Rfc 2865 和2866中 \(IETF\) 指定的 RADIUS 标准的 Microsoft 实现。 作为 RADIUS 服务器，NPS 对许多类型的网络访问执行集中式连接身份验证、授权和记帐，包括无线、身份验证交换机、拨号和虚拟专用网络 \(VPN\) 远程访问和路由器到路由器连接。

> [!NOTE]
> 有关将 NPS 部署为 RADIUS 服务器的信息，请参阅[部署网络策略服务器](nps-deploy.md)。

NPS 支持使用一组异类无线、交换机、远程访问或 VPN 设备。 可以将 NPS 用于远程访问服务，该服务在 Windows Server 2016 中提供。

NPS 使用 Active Directory 域服务 \(AD DS\) 域或本地安全帐户管理器（SAM）用户帐户数据库对用户凭据进行身份验证，以便进行连接尝试。 当运行 NPS 的服务器是 AD DS 域的成员时，NPS 将目录服务用作其用户帐户数据库，并且是单一登录解决方案的一部分。 同一组凭据用于网络访问控制 \(进行身份验证和授权对网络的访问\) 并登录到 AD DS 域。

> [!NOTE]
> NPS 使用用户帐户的拨入属性和网络策略对连接授权。

Internet 服务提供商 \(Isp\) 和维护网络访问的组织在管理各种类型的网络访问时，无论使用何种类型的网络访问设备，都面临着更大的挑战。 RADIUS 标准在同类和异类环境中都支持该功能。 RADIUS 是一种客户端-服务器协议，使得网络访问设备（用作 RADIUS 客户端）可以向 RADIUS 服务器提交身份验证和记帐请求。

RADIUS 服务器具有对用户帐户信息的访问权限，并可以检查网络访问身份验证凭据。 如果对用户凭据进行了身份验证并且连接尝试获得授权，则 RADIUS 服务器会根据指定的条件授权用户访问，然后将网络访问连接记录到一个记帐日志中。 使用 RADIUS 允许在一个中心位置（而不是在每台访问服务器上）收集并维护网络访问用户身份验证、授权和记帐数据。

#### <a name="using-nps-as-a-radius-server"></a>将 NPS 用作 RADIUS 服务器

在以下情况下，您可以使用 NPS 作为 RADIUS 服务器：

- 你使用的是 AD DS 域或本地 SAM 用户帐户数据库作为访问客户端的用户帐户数据库。 
- 你使用的是多个拨号服务器、VPN 服务器或请求拨号路由器上的远程访问，并且你希望同时集中网络策略的配置以及连接日志记录和记帐。 
- 您正在向服务提供商外购拨号、VPN 或无线访问。 访问服务器使用 RADIUS 对您所在组织的成员建立的连接进行身份验证和授权。
- 您要对一组不同种类的访问服务器集中进行身份验证、授权和记帐。

下图显示了将 NPS 用作各种访问客户端的 RADIUS 服务器。 

![作为 RADIUS 服务器的 NPS](../../media/Nps-Server/Nps-Server.jpg)

### <a name="radius-proxy"></a>RADIUS 代理

作为 RADIUS 代理，NPS 将身份验证和记帐消息转发到 NPS 和其他 RADIUS 服务器。 你可以将 NPS 用作 RADIUS 代理，以提供 radius 客户端之间的 RADIUS 消息路由 \(也称为网络访问服务器\) 和为连接尝试执行用户身份验证、授权和记帐的 RADIUS 服务器。 

当用作 RADIUS 代理时，NPS 是一个中央切换点或路由点，其中 RADIUS 访问和记帐消息从中流过。 NPS 将被转发的消息的有关信息记录在记帐日志中。

#### <a name="using-nps-as-a-radius-proxy"></a>将 NPS 用作 RADIUS 代理

出现以下情况，可以将 NPS 用作 RADIUS 代理：

- 你是向多个客户提供外包拨号、VPN 或无线网络访问服务的服务提供商。 你的 Nas 将连接请求发送到 NPS RADIUS 代理。 NPS RADIUS 代理根据连接请求中的用户名的领域部分，将连接请求转发到客户维持的 RADIUS 服务器，并可以对连接尝试进行身份验证和授权。
- 您希望为用户帐户提供身份验证和授权，这些用户帐户不是 NPS 所属域的成员，也不是与 NPS 所属的域具有双向信任关系的另一个域。 这包括未受信任域、单向受信任域和其他林中的帐户。 不是将访问服务器配置为将其连接请求发送到 NPS RADIUS 服务器，而是将它们配置为将其连接请求发送到 NPS RADIUS 代理。 NPS RADIUS 代理使用用户名的领域名称部分，并将请求转发到正确域或林中的 NPS。 在一个域或林中的用户帐户的连接尝试可以在另一个域或林中为 Nas 进行身份验证。
- 您希望使用不是 Windows 帐户数据库的数据库执行身份验证和授权。 在这种情况下，与指定领域名称匹配的连接请求转发到 RADIUS 服务器，后者拥有对不同用户帐户和授权数据数据库的访问权限。 其他用户数据库示例包括 Novell Directory Services (NDS) 和结构化查询语言 (SQL) 数据库。
- 您希望处理大量连接请求。 在这种情况下，可以不将 RADIUS 客户端配置为尝试跨多个 RADIUS 服务器平衡其连接和记帐请求，而将它们配置为将其连接和记帐请求发送到 NPS RADIUS 代理。 NPS RADIUS 代理动态地平衡跨多个 RADIUS 服务器的连接和记帐请求负载，并增加每秒处理的大量 RADIUS 客户端和身份验证数。
- 您希望向外包服务提供商提供 RADIUS 身份验证和授权，并最大限度减少 Intranet 防火墙配置。 Intranet 防火墙介于外围网络（Intranet 和 Internet 之间的网络）和 Intranet 之间。 通过在外围网络中放置 NPS，外围网络和 intranet 之间的防火墙必须允许流量在 NPS 和多个域控制器之间流动。 通过将 NPS 替换为 NPS 代理，防火墙必须仅允许在 NPS 代理和 intranet 中的一个或多个 NPSs 之间流动 RADIUS 流量。

下图显示了 NPS 作为 radius 客户端和 RADIUS 服务器之间的 RADIUS 代理。

![作为 RADIUS 代理的 NPS](../../media/Nps-Proxy/Nps-Proxy.jpg)

使用 NPS，各组织还可以在保留对用户身份验证、授权和记帐活动控制的同时，将远程访问基础结构外包给服务提供商。

可以为下列方案创建 NPS 配置：

- 无线访问
- 组织拨号或虚拟专用网络 (VPN) 远程访问
- 外包拨号或无线访问
- Internet 访问权限
- 对业务合作伙伴 Extranet 资源的经过身份验证的访问

## <a name="radius-server-and-radius-proxy-configuration-examples"></a>RADIUS 服务器和 RADIUS 代理配置示例

以下配置示例演示如何将 NPS 配置成 RADIUS 服务器和 RADIUS 代理。

**作为 RADIUS 服务器的 NPS**。 在此示例中，NPS 配置为 RADIUS 服务器，默认连接请求策略是唯一配置的策略，所有连接请求均由本地 NPS 处理。 NPS 可以对其帐户位于 NPS 域和受信任域中的用户进行身份验证和授权。

**作为 RADIUS 代理的 NPS**。 在此示例中，NPS 配置为 RADIUS 代理，用于将连接请求转发到两个不受信任的域中的远程 RADIUS 服务器组。 将删除默认连接请求策略，并创建两个新的连接请求策略，以将请求转发到两个不受信任的域中的每个域。 在此示例中，NPS 不处理本地服务器上的任何连接请求。 

**NPS 同时作为 radius 服务器和 radius 代理**。 除了可以指定在本地处理连接请求的默认连接请求策略之外，还创建了一个新的连接请求策略，以将连接请求转发到未受信任域中的 NPS 或其他 RADIUS 服务器。 此处的第二个策略命名为代理策略。 在此示例中，代理策略首先出现在策略的有序列表中。 如果连接请求与代理策略相匹配，则会将连接请求转发到远程 RADIUS 服务器组中的 RADIUS 服务器。 如果连接请求与代理策略不匹配，但与默认连接请求策略相匹配，则 NPS 会处理本地服务器上的连接请求。 如果连接请求与任一策略不匹配，则丢弃该连接请求。

**使用远程记帐服务器作为 RADIUS 服务器的 NPS**。 在此示例中，未将本地 NPS 配置为执行记帐，并修改了默认连接请求策略，以便将 RADIUS 记帐消息转发到远程 RADIUS 服务器组中的 NPS 或其他 RADIUS 服务器。 尽管转发记帐消息，但不会转发身份验证和授权消息，并且本地 NPS 将为本地域和所有受信任域执行这些功能。

**具有远程 RADIUS 到 Windows 用户映射的 NPS**。 在此示例中，通过将身份验证请求转发到远程 RADIUS 服务器，并同时使用本地 Windows 用户帐户进行授权，NPS 同时充当了每个单个连接请求的 RADIUS 服务器和 RADIUS 代理。 通过将“远程 RADIUS 到 Windows 用户映射”属性配置为连接请求策略的条件，从而实现此配置。 \(此外，必须在 RADIUS 服务器上以本地方式创建一个用户帐户，该服务器与远程用户帐户具有相同的名称，远程 RADIUS 服务器使用该帐户进行身份验证。\)

## <a name="configuration"></a>配置

若要将 NPS 配置为 RADIUS 服务器，你可以在 NPS 控制台或服务器管理器中使用标准配置或高级配置。 若要将 NPS 配置为 RADIUS 代理，则必须使用高级配置。

### <a name="standard-configuration"></a>标准配置

使用标准配置将提供向导，有助于针对以下方案配置 NPS：

- 用于拨号或 VPN 连接的 RADIUS 服务器
- 用于 802.1X 无线或有线连接的 RADIUS 服务器

若要使用向导配置 NPS，请打开 NPS 控制台，选择上述方案之一，然后单击打开向导的链接。

### <a name="advanced-configuration"></a>高级配置

使用高级配置时，将 NPS 手动配置为 RADIUS 服务器或 RADIUS 代理。 

若要使用高级配置来配置 NPS，请打开 NPS 控制台，然后单击 "**高级配置**" 旁边的箭头以展开此部分。

将提供以下高级配置项。

#### <a name="configure-radius-server"></a>配置 RADIUS 服务器

若要将 NPS 配置为 RADIUS 服务器，您必须配置 RADIUS 客户端、网络策略和 RADIUS 记帐。

有关进行这些配置的说明，请参阅以下主题。

- [配置 RADIUS 客户端](nps-radius-clients-configure.md)
- [配置网络策略](nps-np-configure.md)
- [配置网络策略服务器记帐](nps-accounting-configure.md)

#### <a name="configure-radius-proxy"></a>配置 RADIUS 代理

若要将 NPS 配置为 RADIUS 代理，您必须配置 RADIUS 客户端、远程 RADIUS 服务器组和连接请求策略。

有关进行这些配置的说明，请参阅以下主题。

- [配置 RADIUS 客户端](nps-radius-clients-configure.md)
- [配置远程 RADIUS 服务器组](nps-crp-rrsg-configure.md)
- [配置连接请求策略](nps-crp-configure.md)

## <a name="nps-logging"></a>NPS 日志记录

NPS 日志记录也称为 "RADIUS 记帐"。 根据你的需求配置 NPS 日志记录是否将 NPS 用作 RADIUS 服务器、代理或这些配置的任意组合。

若要配置 NPS 日志记录，必须配置要用事件查看器记录和查看的事件，然后确定要记录的其他信息。 另外，还必须决定是将用户身份验证和记帐信息记录到本地计算机上存储的文本日志文件中，还是记录到本地计算机或远程计算机的 SQL Server 数据库中。

有关详细信息，请参阅[配置网络策略服务器记帐](nps-accounting-configure.md)。
