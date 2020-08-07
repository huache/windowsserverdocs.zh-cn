---
ms.assetid: 1a6740e6-5b6d-41f8-9ec4-32cdbee3e1bb
title: 外围网络和 Internet 客户端的名称解析
author: billmath
manager: femila
ms.date: 04/13/2020
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 050d1ddd8d04e288c6e480bed2d9e24146198020
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972124"
---
# <a name="name-resolution-for-perimeter-and-internet-clients"></a>外围网络和 Internet 客户端的名称解析


因此，若 \( \) 要在一个或多个域名系统 \( DNS \) 区域同时为外围网络和 Internet 客户端提供服务的 Active Directory 联合身份验证服务 AD FS 方案中，名称解析可以成功运行，必须完成以下任务：

-   必须配置要控制的 Internet 区域中的 DNS，以将 AD FS 主机名的所有 Internet 客户端请求解析为联合服务器代理。 若要实现此目的，请将主机 \( a \) 资源记录添加到联合服务器代理的 Internet DNS 区域。

-   外围网络中的 DNS 必须配置为将 AD FS 主机名的所有传入客户端请求解析为联合服务器。 若要实现此目的，请将主机 \( a \) 资源记录添加到联合服务器代理的外围 DNS 区域。

> [!NOTE]
> 假设已 \( \) 在公司网络 DNS 中创建了联合服务器的主机 a 资源记录。 如果此记录尚不存在，请创建此记录，然后执行这些过程。 有关如何为 \( 联合服务器创建主机 a 资源记录的详细信息 \) ，请参阅[向联合服务器的企业 DNS 添加主机 &#40;&#41; 资源记录](Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)。

## <a name="add-a-host-a-resource-record-to-the-internet-dns-zone-for-a-federation-server-proxy"></a>将主机 \( a \) 资源记录添加到联合服务器代理的 Internet DNS 区域
为了使 Internet 上的客户端计算机可以通过新部署的联合服务器代理成功访问联合服务器，你必须首先 \( \) 在你控制的 Internet DNS 区域中创建一个主机 a 资源记录。 此资源记录将帐户联合服务器的主机名 \( （例如 fs.fabrikam.com）解析 \) 为帐户联合服务器代理的 IP 地址 \( （例如， \) 在外围网络中的131.107.27.68）。

> [!NOTE]
> 假设你使用的 DNS 服务器运行 Windows 2000 Server、Windows Server 2003 或 Windows Server 2008 with DNS 服务器服务来控制 Internet DNS 区域。

**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

#### <a name="to-add-a-host-a-resource-record-to-the-internet-dns-zone-for-a-federation-server-proxy"></a>将主机 \( a \) 资源记录添加到联合服务器代理的 Internet DNS 区域

1.  在 DNS 服务器上，打开 DNS 管理单元 \- 。

2.  在控制台树中，右键 \- 单击适用的正向查找区域，然后单击 "**新建主机 \( A 或 \) AAAA**"。

3.  在 "**名称**" 中，仅键入联合服务器的计算机名称。 例如，对于完全限定的域名 \( FQDN \) fs.fabrikam.com，键入**fs**。

4.  在 " **IP 地址**" 中，键入新联合服务器代理的 IP 地址，例如131.107.27.68。

5.  单击 **“添加主机”**。

## <a name="add-a-host-a-resource-record-to-the-perimeter-dns-zone-for-a-federation-server-proxy"></a>为 \( \) 联合服务器代理将主机 a 资源记录添加到外围 DNS 区域
为了使 Internet 客户端请求可由联合服务器代理成功处理并在由 Internet DNS 区域解析后访问联合服务器，你必须 \( \) 在外围 DNS 区域中创建主机 a 资源记录。 此资源记录解析帐户联合服务器的主机名 \( ，例如 fs。 fabrikam.com \) 帐户联合服务器的 IP 地址 \( （例如， \) 企业网络中的192.168.1.4）。

> [!NOTE]
> 假设你正在使用运行 Windows 2000 Server、Windows Server 2003、Windows Server 2008 或 Windows Server 2012 的 DNS 服务器 &reg; 来控制外围 DNS 区域。

**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

#### <a name="to-add-a-host-a-resource-record-to-the-perimeter-dns-zone-for-a-federation-server-proxy"></a>为 \( \) 联合服务器代理将主机 a 资源记录添加到外围 DNS 区域

1.  在外围网络的 DNS 服务器上，打开**dns 管理单元 \- **。

2.  在控制台树中，右键 \- 单击适用的正向查找区域，然后单击 "**新建主机 \( A 或 \) AAAA**"。

3.  在 "**名称**" 中，仅键入联合服务器的计算机名称。 例如，对于 FQDN fs.fabrikam.com，请键入 **fs**。

4.  在 " **IP 地址**" 文本框中，键入企业网络中联合服务器的 IP 地址，例如192.168.1.4。

5.  单击 **“添加主机”**。

## <a name="additional-references"></a>其他参考
[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)

[联合服务器代理的名称解析要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055(v=ws.11))

