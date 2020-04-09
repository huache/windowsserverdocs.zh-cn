---
ms.assetid: b7109e46-b66e-4c5c-8b87-a6611d68415a
title: 在仅为外围网络提供服务的 DNS 区域中为联合服务器代理配置名称解析
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 451ed2bb2b2da9481d33c6e9e339bb582824a4e1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854920"
---
# <a name="configure-name-resolution-for-a-federation-server-proxy-in-a-dns-zone-that-serves-only-the-perimeter-network"></a>在仅为外围网络提供服务的 DNS 区域中为联合服务器代理配置名称解析


因此，名称解析可以成功地在 Active Directory 联合身份验证服务 \(中的联合服务器上工作 AD FS\) 方案，其中一个或多个域名系统 \(DNS\) 区域仅提供外围网络，必须完成以下任务：  
  
-   必须更新联合服务器代理上的 hosts 文件，才能添加联合服务器的 IP 地址。  
  
-   外围网络中的 DNS 必须配置为将 AD FS 主机名的所有客户端请求解析为联合服务器代理。 为此，请将一个主机 \(\) 资源记录添加到联合服务器代理的外围 DNS 中。  
  
> [!NOTE]  
> 这些过程假定已在公司网络 DNS 中为联合服务器 \(了\) 的资源记录。 如果此记录尚不存在，请创建此记录，然后执行这些过程。 有关如何为联合服务器 \(\) 资源记录创建主机的详细信息，请参阅[向联合服务器的企业 DNS &#40;添加&#41;主机 a 资源记录](Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)。  
  
## <a name="add-the-ip-address-of-a-federation-server-to-the-hosts-file"></a>将联合服务器的 IP 地址添加到 hosts 文件  
为了使联合服务器代理在帐户伙伴的外围网络中能够按预期运行，必须在该联合服务器代理上的 hosts 文件中添加一个条目，指向联合服务器的 DNS 主机名 \(例如，fs.fabrikam.com\) 和 IP 地址 \(例如，帐户伙伴的企业网络中的 192.168.1.4\)。 如果将此条目添加到 hosts 文件中，联合服务器代理将无法与自身联系以解析客户端\-启动对帐户伙伴中的联合服务器的调用。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
#### <a name="to-add-the-ip-address-of-a-federation-server-to-the-hosts-file"></a>将联合服务器的 IP 地址添加到 hosts 文件  
  
1.  导航到% systemroot%\\Winnt\\System32\\驱动程序目录文件夹并找到**hosts**文件。  
  
2.  启动记事本，然后打开 **hosts** 文件。  
  
3.  将帐户伙伴中的联合服务器的 IP 地址和主机名添加到**hosts**文件中，如以下示例中所示：  
  
    **192.168.1.4fs.fabrikam.com**  
  
4.  保存并关闭该文件。  
  
## <a name="add-a-host-a-resource-record-to-perimeter-dns-for-a-federation-server-proxy"></a>为联合服务器代理将主机 \(\) 资源记录添加到外围 DNS  
为了使 Internet 上的客户端可以通过新部署的联合服务器代理成功访问联合服务器，你必须首先在外围 DNS 中创建一个 \(\) 资源记录的主机。 此资源记录解析帐户联合服务器 \(的主机名，例如，fs.fabrikam.com\) 到帐户联合服务器代理的 IP 地址 \(例如，外围网络中的 131.107.27.68\)。  
  
> [!NOTE]  
> 假设你正在使用运行 Windows 2000 Server、Windows Server 2003 或 Windows Server 2008 和 DNS 服务器服务的 DNS 服务器来控制外围 DNS 区域。  
  
**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
#### <a name="to-add-a-host-a-resource-record-to-perimeter-dns-for-a-federation-server-proxy"></a>为联合服务器代理向外围 DNS 添加主机 \(\) 资源记录  
  
1.  在外围网络的 DNS 服务器上，打开中的 DNS snap\-。 单击 "**开始**"，指向 "**管理工具**"，然后单击 " **DNS**"。  
  
2.  在控制台树中，\-右键单击适用的正向查找区域，然后单击 "**新建主机 \(A 或 AAAA\)** "。  
  
3.  在 "**名称**" 中，仅键入联合服务器的计算机名称。 例如，对于完全限定的域名 \(FQDN\) fs.fabrikam.com，请键入**fs**。  
  
4.  在 " **IP 地址**" 中，键入新联合服务器代理的 IP 地址，例如**131.107.27.68**。  
  
5.  单击 **“添加主机”** 。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  
[联合服务器代理的名称解析要求](https://technet.microsoft.com/library/dd807055.aspx)  
  

