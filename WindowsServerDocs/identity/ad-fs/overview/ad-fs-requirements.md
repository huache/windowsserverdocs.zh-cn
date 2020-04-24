---
ms.assetid: 28f4a518-1341-4a10-8a4e-5f84625b314b
title: AD FS 2016 要求
description: 安装 Active Directory 联合身份验证服务的要求。
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 03/06/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: a2f4c9ac05e72083fab3e3a926dbdd2876214a7b
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "77517532"
---
# <a name="ad-fs-requirements"></a>AD FS 要求



部署 AD FS 的要求如下：  
  
-   [证书要求](ad-fs-requirements.md#BKMK_1)  
  
-   [硬件要求](ad-fs-requirements.md#BKMK_2)  
  
-   [代理要求](ad-fs-requirements.md#BKMK_3)  
  
-   [AD DS 要求](ad-fs-requirements.md#BKMK_4)  
  
-   [配置数据库要求](ad-fs-requirements.md#BKMK_5)  
  
-   [浏览器要求](ad-fs-requirements.md#BKMK_6)  

-   [网络要求](ad-fs-requirements.md#BKMK_7)  
  
-   [权限要求](ad-fs-requirements.md#BKMK_13)  
  
## <a name="certificate-requirements"></a><a name="BKMK_1"></a>证书要求  
  
### <a name="ssl-certificates"></a>SSL 证书

每个 AD FS 和 Web 应用程序代理服务器都有一个 SSL 证书，用于向联合身份验证服务发送 HTTPS 请求。  Web 应用程序代理可以有用于向发布的应用程序发送请求的其他 SSL 证书。

**建议：** 对所有 AD FS 联合服务器和 Web 应用程序代理使用相同的 SSL 证书。 

**要求：**

联合服务器上的 SSL 证书必须满足以下要求
- 证书是公开的且受信任的证书（适用于生产部署）
- 证书包含服务器身份验证增强型密钥使用 (EKU) 值
- 证书在使用者或使用者可选名称 (SAN) 中包含联合身份验证服务名称，例如“fs.contoso.com”
- 对于端口 443 上的用户证书身份验证，证书包含“certauth.\<federation service name\>”，例如 SAN 中的“certauth.fs.contoso.com”
- 对于使用 Windows 10 之前版本客户端进行设备注册或对本地资源进行新式身份验证，SAN 必须为组织中使用的每个 UPN 后缀包含“enterpriseregistration.\<upn suffix\>”。

Web 应用程序代理上的 SSL 证书必须满足以下要求
- 如果代理用于代理使用 Windows 集成身份验证的 AD FS 请求，则代理 SSL 证书必须与联合服务器 SSL 证书相同（使用相同的密钥）
- 如果启用了 AD FS 属性“ExtendedProtectionTokenCheck”（AD FS 中的默认设置），则代理 SSL 证书必须与联合服务器 SSL 证书相同（使用相同的密钥）
- 否则，代理 SSL 证书的要求与联合服务器 SSL 证书的要求相同

### <a name="service-communication-certificate"></a>服务通信证书
大多数 AD FS 方案（包括 Azure AD 和 Office 365）都不需要此证书。 默认情况下，AD FS 将初始配置时提供的 SSL 证书配置为服务通信证书。

**建议：**
- 使用与 SSL 相同的证书。  

### <a name="token-signing-certificate"></a>令牌签名证书
此证书用于向信赖方签名颁发的令牌，因此信赖方应用程序必须将该证书及其关联密钥识别为已知且受信任。 令牌签名证书更改时（例如，证书过期和配置新证书时），必须更新所有信赖方。

**建议：** 使用 AD FS 默认的、内部生成的自签名令牌签名证书。  

**要求：**
- 如果你的组织要求使用企业 PKI 中的证书进行令牌签名，则可以使用 Install-AdfsFarm cmdlet 的 SigningCertificateThumbprint 参数来完成此操作。
- 无论使用的是默认内部生成的证书还是外部注册的证书，在更改令牌签名证书时，必须确保所有信赖方都更新了新的证书信息。  否则，将无法登录到任何未更新的信赖方。

### <a name="token-encryptingdecrypting-certificate"></a>令牌加密/解密证书
此证书由加密颁发给 AD FS 令牌的声明提供程序使用。

**建议：** 使用 AD FS 默认的、内部生成的自签名令牌解密证书。  

**要求：**
- 如果你的组织要求使用企业 PKI 中的证书进行令牌签名，则可以使用 Install-AdfsFarm cmdlet 的 DecryptingCertificateThumbprint 参数来完成此操作。
- 无论使用的是默认的内部生成的证书还是外部注册的证书，在更改令牌解密证书时，必须确保所有声明提供程序都更新了新的证书信息。  否则，使用未更新的任何声明提供程序登录将失败。
  
> [!CAUTION]  
> 用于令牌签名和令牌解密\/加密的证书对联合身份验证服务的稳定性至关重要。 管理自己的令牌签名和令牌解密\/加密证书的客户应确认是否备份了这些证书且这些证书是否可在恢复事件期间单独使用。  

### <a name="user-certificates"></a>用户证书
- 将 x509 用户证书身份验证用于 AD FS 时，所有用户证书必须链接到 AD FS 和 Web 应用程序代理服务器信任的根证书颁发机构。

## <a name="hardware-requirements"></a><a name="BKMK_2"></a>硬件要求  
AD FS 和 Web 应用程序代理硬件要求（物理要求或虚拟要求）都根据 CPU 而定，因此，你应调整场的大小以提供处理容量。  
- 使用 [AD FS 2016 容量计划电子表格](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)确定所需的 AD FS 和 Web 应用程序代理服务器的数量。

AD FS 的内存和磁盘要求稳定不变，请参阅下表：


|**硬件要求**|**最低要求**|**建议的要求**|
|----- | ----- |-----|
|RAM|2 GB|4 GB |
|磁盘空间|32 GB|100 GB |

**SQL Server 硬件要求**

如果将 SQL Server 用于 AD FS 配置数据库，请根据最基本的 SQL Server 建议调整 SQL Server 的大小。  AD FS 数据库非常小，并且 AD FS 不会对数据库实例进行大量的处理负载。  但 AD FS 确实会在身份验证过程中多次连接到数据库，因此网络连接应是可靠的。  遗憾的是，AD FS 配置数据库不支持 SQL Azure。
  
## <a name="proxy-requirements"></a><a name="BKMK_3"></a>代理要求  
  
-   对于 Extranet 访问，必须部署属于远程访问服务器角色的 Web 应用程序代理角色服务。 

-   第三方代理必须支持 [MS-ADFSPIP 协议](https://msdn.microsoft.com/library/dn392811.aspx)，才能作为 AD FS 代理受到支持。  有关第三方供应商的列表，请参阅[常见问题解答](AD-FS-FAQ.md)。

-   AD FS 2016 需要 Windows Server 2016 上的 Web 应用程序代理服务器。  不能为在 2016 场行为级别运行的 AD FS 2016 场配置下级代理。
  
-   不能在同一台计算机上安装联合服务器和 Web 应用程序代理角色服务。  
  
## <a name="ad-ds-requirements"></a><a name="BKMK_4"></a>AD DS 要求  
**域控制器要求**  
  
- AD FS 需要运行 Windows Server 2008 或更高版本的域控制器。

- Microsoft Passport for Work 至少需要一个 Windows Server 2016 域控制器。
  
> [!NOTE]  
> 对 Windows Server 2003 域控制器环境的所有支持均已终止。 有关 Microsoft 支持生命周期的其他信息，请访问[此页面](https://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows+Server+2003&Filter=FilterNO)。  
  
**域功能级别要求**  
  
 - 所有用户帐户域和 AD FS 服务器加入的域必须在 Windows Server 2003 或更高版本的域功能级别上运行。  
  
 - 如果证书明确映射到 AD DS 中的用户帐户，则客户端证书身份验证需要 Windows Server 2008 或更高版本的域功能级别。  
  
**架构要求**  
  
-   AD FS 2016 的新安装需要Active Directory 2016 架构（最低版本为 85）。

-   将 AD FS 场行为级别 (FBL) 提升到 2016 级别需要 Active Directory 2016 架构（最低版本为 85）。  

  
**服务帐户要求**  
  
-   任何标准域帐户都可以用作 AD FS 的服务帐户。 也支持组托管服务帐户托管服务帐户。 配置 AD FS 时，将自动添加运行时所需的权限。

-   AD 服务帐户所需的用户权限分配是“以服务身份登录”

-   “NT Service\adfssrv”和“NT Service\drs”所需的用户权限分配是“生成安全审核”和“以服务身份登录”。

-   组托管服务帐户需要至少一个运行 Windows Server 2012 或更高版本的域控制器。  GMSA 必须位于默认的“CN=Managed Service Accounts”容器下。  

-   对于 Kerberos 身份验证，服务主体名称“`HOST/<adfs\_service\_name>`”必须在 AD FS 服务帐户上进行注册。 默认情况下，创建新的 AD FS 场时，AD FS 将配置此设置。  如果此操作失败（例如发生冲突或权限不足的情况），你将看到一条警告，且应手动添加它。  
   
**域要求**  
  
-   所有 AD FS 服务器都必须加入 AD DS 域。  
  
-   场中的所有 AD FS 服务器都必须部署在同一个域中。  
   
**多林要求**  
  
-   AD FS 服务器加入的域必须信任包含向 AD FS 服务进行身份验证的用户的每个域或林。  

-   AD FS 服务帐户所属的林必须信任所有用户登录林。 
  
-   AD FS 服务帐户必须具有读取包含对 AD FS 服务进行用户身份验证的每个域中用户属性的权限。  
  
## <a name="configuration-database-requirements"></a><a name="BKMK_5"></a>配置数据库要求  
本部分介绍分别使用 Windows 内部数据库 (WID) 或 SQL Server 数据库作为数据库的 AD FS 场的要求和限制：  
  
**WID**  
  
-   WID 场不支持 SAML 2.0 的项目解析配置文件。    

-   WID 场不支持令牌重放检测。 （此功能仅在 AD FS 充当联合身份验证提供程序并使用来自外部声明提供程序的安全令牌的情况下使用。）  
  
下表汇总了 WID 与 SQL Server 场中支持的 AD FS 服务器数。    
  
  
|| 在 AD FS 中配置了 1 - 100 个信赖方 (RP) 信任 | 配置了 100 个以上的 RP 信任  |
| --- |--- | --- |
|1 - 30 个 AD FS 服务器|支持 WID|不支持使用 WID（需要 SQL Server） |
|超过 30 个 AD FS 服务器|不支持使用 WID（需要 SQL Server）|不支持使用 WID（需要 SQL Server）  
  
**SQL Server**  
  
- Windows Server 2016 中的 AD FS 支持 SQL Server 2008 及更高版本。

- SQL Server 场支持 SAML 项目解析和令牌重放检测。  
  
## <a name="browser-requirements"></a><a name="BKMK_6"></a>浏览器要求  
通过浏览器或浏览器控件执行 AD FS 身份验证时，浏览器必须符合遵守以下要求：  
  
- 必须启用 JavaScript  
  
- 对于单一登录，必须将客户端浏览器配置为允许 Cookie  
  
- 必须支持服务器名称指示 \(SNI\)  
  
- 对于用户证书和设备证书身份验证，浏览器必须支持 SSL 客户端证书身份验证  

- 若要使用 Windows 集成身份验证进行无缝登录，必须在本地 Intranet 区域或受信任的站点区域中配置联合身份验证服务名称（例如 https:\/\/fs.contoso.com）。
  ## <a name="network-requirements"></a><a name="BKMK_7"></a>网络要求  
 
**防火墙要求**  
  
位于 Web 应用程序代理和联合服务器场之间的防火墙以及客户端和 Web 应用程序代理之间的防火墙都必须启用 TCP 端口 443 入站。  
  
此外，如果需要客户端用户证书身份验证\(使用 X509 用户证书的 clientTLS 身份验证\)，并且未启用端口 443 上的 certauth 终结点，则 AD FS 2016 要求在客户端和 Web 应用程序代理之间的防火墙上启用 TCP 端口 49443 入站。 无需在 Web 应用程序代理和联合服务器之间的防火墙上执行此操作。 

有关混合端口要求的其他信息，请参阅 [混合标识端口和协议](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-ports)。 

有关其他信息，请参阅[保护 Active Directory 联合身份验证服务的最佳做法](../deployment/Best-Practices-Securing-AD-FS.md)
  
**DNS 要求**  
  
-   对于 Intranet 访问，在内部公司网络 \(Intranet\) 中访问 AD FS 服务的所有客户端必须能够将 AD FS 服务名称解析为多个或单个 AD FS 服务器的负载均衡器。  
  
-   对于 Extranet 访问，所有从公司网络 \(extranet\/internet\) 外部访问 AD FS 服务的客户端必须能够将 AD FS 服务名称解析为多个或单个 Web 应用程序代理服务器的负载均衡器。  
  
-   DMZ 中的每个 Web 应用程序代理服务器都必须能够将 AD FS 服务名称解析为多个或单个 AD FS 服务器的负载均衡器。 可使用 DMZ 网络中的备用 DNS 服务器或使用 HOSTS 文件更改本地服务器分辨率来实现这一操作。  
  
-   对于 Windows 集成身份验证，必须将 DNS A 记录\(而不是 CNAME\)用作联合身份验证服务名称。  

-   对于端口 443 上的用户证书身份验证，必须在 DNS 中配置“certauth.\<federation service name\>”才能解析为联合服务器或 Web 应用程序代理。

-   对于使用 Windows 10 之前版本客户端进行设备注册或对本地资源进行新式身份验证，必须为组织中使用的每个 UPN 后缀配置“enterpriseregistration.\<upn suffix\>”才能解析联合服务器或 Web 应用程序代理。

**负载均衡器要求**
- 负载均衡器不得终止 SSL。 AD FS 支持具有证书身份验证的多个用例，这些用例在终止 SSL 时会中断。 任何用例都不支持在负载均衡器上终止 SSL。 
- 建议使用支持 SNI 的负载均衡器。 如果不是这样，则在 AD FS/Web 应用程序代理服务器上使用 0.0.0.0 回退绑定应该可以解决这一问题。
- 建议使用 HTTP（而不使用 HTTPS）运行状况探测终结点对路由流量执行负载均衡器运行状况检查。 这样可以避免任何与 SNI 有关的问题。 对这些探测终结点的响应是 HTTP 200 OK，并且在本地提供，而不依赖于后端服务。 可以使用路径“/adfs/probe”通过 HTTP 访问 HTTP 探测
    - http://&lt;Web Application Proxy name&gt;/adfs/probe
    - http://&lt;ADFS server name&gt;/adfs/probe
    - http://&lt;Web Application Proxy IP address&gt;/adfs/probe
    - http://&lt;ADFS IP address&gt;/adfs/probe
- 不建议使用 DNS 轮循机制作为负载均衡的方法。 使用这种类型的负载均衡不提供使用运行状况探测从负载均衡器中删除节点的自动化方法。 
- 不建议在负载均衡器中使用基于 IP 的会话相关性或停滞会话对到 AD FS 的流量进行身份验证。 使用邮件客户端的旧身份验证协议连接到 Office 365 邮件服务 (Exchange Online) 时，这可能会导致某些节点重载。 

## <a name="permissions-requirements"></a><a name="BKMK_13"></a>权限要求  
执行 AD FS 的安装和初始配置的管理员必须具有 AD FS 服务器上的本地管理员权限。  如果本地管理员无权在 Active Directory 中创建对象，则他们必须先具有域管理员身份才能创建所需的 AD 对象，然后使用 AdminConfiguration 参数配置 AD FS 场。  
  
  

