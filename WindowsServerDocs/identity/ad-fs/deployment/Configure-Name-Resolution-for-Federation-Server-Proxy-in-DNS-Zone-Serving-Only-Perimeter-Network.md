---
ms.assetid: b7109e46-b66e-4c5c-8b87-a6611d68415a
title: 在仅为外围网络提供服务的 DNS 区域中为联合服务器代理配置名称解析
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: ed30d26225894fd12fbb007d9c1463de15af64dc
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938415"
---
# <a name="configure-name-resolution-for-a-federation-server-proxy-in-a-dns-zone-that-serves-only-the-perimeter-network"></a>在仅为外围网络提供服务的 DNS 区域中为联合服务器代理配置名称解析


因此，名称解析可以在 Active Directory 联合身份验证服务 AD FS 方案中成功地运行联合 \( 服务器 \) ，其中一个或多个域名系统 \( DNS \) 区域只为外围网络提供服务，必须完成以下任务：

-   必须更新联合服务器代理上的 hosts 文件，才能添加联合服务器的 IP 地址。

-   外围网络中的 DNS 必须配置为将 AD FS 主机名的所有客户端请求解析为联合服务器代理。 为此，请为 \( \) 联合服务器代理向外围 DNS 添加主机 a 资源记录。

> [!NOTE]
> 这些过程假定已 \( \) 在公司网络 DNS 中创建联合服务器的主机 a 资源记录。 如果此记录尚不存在，请创建此记录，然后执行这些过程。 有关如何为 \( 联合服务器创建主机 A 资源记录的详细信息 \) ，请参阅[向联合服务器的企业 DNS 添加主机 &#40;&#41; 资源记录](Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)。

## <a name="add-the-ip-address-of-a-federation-server-to-the-hosts-file"></a>将联合服务器的 IP 地址添加到 hosts 文件
为了使联合服务器代理在帐户伙伴的外围网络中能够按预期运行，必须在该联合服务器代理上的 hosts 文件中添加一个条目，指向联合服务器的 DNS 主机名 \( （例如，fs.fabrikam.com \) 和 IP 地址， \( 例如， \) 帐户伙伴的企业网络中的192.168.1.4）。 如果将此条目添加到 hosts 文件中，联合服务器代理将无法与自身联系以解析客户端 \- 发起的对帐户伙伴中的联合服务器的调用。

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

#### <a name="to-add-the-ip-address-of-a-federation-server-to-the-hosts-file"></a>将联合服务器的 IP 地址添加到 hosts 文件

1.  导航到% systemroot% \\ Winnt \\ System32 \\ 驱动程序目录文件夹并找到**hosts**文件。

2.  启动记事本，然后打开 **hosts** 文件。

3.  将帐户伙伴中的联合服务器的 IP 地址和主机名添加到**hosts**文件中，如以下示例中所示：

    **192.168.1.4fs.fabrikam.com**

4.  保存并关闭文件。

## <a name="add-a-host-a-resource-record-to-perimeter-dns-for-a-federation-server-proxy"></a>为 \( \) 联合服务器代理向外围 DNS 添加主机 a 资源记录
为了使 Internet 上的客户端可以通过新部署的联合服务器代理成功访问联合服务器，你必须首先 \( \) 在外围 DNS 中创建 a 主机资源记录。 此资源记录将帐户联合服务器的主机名 \( （例如 fs.fabrikam.com）解析 \) 为帐户联合服务器代理的 IP 地址 \( （例如， \) 在外围网络中的131.107.27.68）。

> [!NOTE]
> 假设你正在使用运行 Windows 2000 Server、Windows Server 2003 或 Windows Server 2008 和 DNS 服务器服务的 DNS 服务器来控制外围 DNS 区域。

**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

#### <a name="to-add-a-host-a-resource-record-to-perimeter-dns-for-a-federation-server-proxy"></a>为 \( \) 联合服务器代理向外围 DNS 添加主机 a 资源记录

1.  在外围网络的 DNS 服务器上，打开 DNS 管理单元 \- 。 单击 "**开始**"，指向 "**管理工具**"，然后单击 " **DNS**"。

2.  在控制台树中，右键 \- 单击适用的正向查找区域，然后单击 "**新建主机 \( A 或 \) AAAA**"。

3.  在 "**名称**" 中，仅键入联合服务器的计算机名称。 例如，对于完全限定的域名 \( FQDN \) fs.fabrikam.com，键入**fs**。

4.  在 " **IP 地址**" 中，键入新联合服务器代理的 IP 地址，例如**131.107.27.68**。

5.  单击 **“添加主机”**。

## <a name="additional-references"></a>其他参考
[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)

[联合服务器代理的名称解析要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055(v=ws.11))

