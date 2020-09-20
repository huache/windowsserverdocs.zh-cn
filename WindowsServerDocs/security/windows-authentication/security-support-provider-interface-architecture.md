---
title: 安全支持提供程序接口体系结构
description: Windows Server 安全
ms.topic: article
ms.assetid: de09e099-5711-48f8-adbd-e7b8093a0336
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: da7c390427a3f0f2348d91e14d0affef905db390
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766950"
---
# <a name="security-support-provider-interface-architecture"></a>安全支持提供程序接口体系结构

>适用于：Windows Server（半年频道）、Windows Server 2016

本参考主题面向 IT 专业人员，介绍了在安全支持提供程序界面内使用的 Windows 身份验证协议， (SSPI) 体系结构。

Microsoft 安全支持提供程序接口 (SSPI) 是 Windows 身份验证的基础。 要求身份验证的应用程序和基础结构服务会使用 SSPI 提供它。

SSPI 是通用安全服务 API 在 Windows Server 操作系统中 (GSSAPI) 的实现。 有关 GSSAPI 的详细信息，请参阅 IETF RFC 数据库中的 RFC 2743 和 RFC 2744。

调用 Windows 中特定身份验证协议 (Ssp) 的默认安全支持提供程序将作为 Dll 合并到 SSPI。 以下各节介绍了这些默认的 Ssp。 如果可以对 SSPI 进行操作，则可以合并其他 Ssp。

如下图所示，Windows 中的 SSPI 提供一种机制，该机制通过客户端计算机和服务器之间的现有通信通道携带身份验证令牌。 当需要对两台计算机或设备进行身份验证，以便它们能够安全地通信时，针对身份验证的请求会路由到 SSPI，后者完成身份验证过程，而不考虑当前使用的网络协议。 SSPI 返回透明的二进制大型对象。 它们在应用程序之间传递，在这种情况下，它们可以传递到 SSPI 层。 因此，SSPI 允许应用程序使用计算机或网络上可用的各种安全模型，而无需更改安全系统的接口。

![显示安全支持提供程序接口体系结构的关系图](../media/security-support-provider-interface-architecture/AuthN_SecuritySupportProviderInterfaceArchitecture.jpg)

以下各节介绍与 SSPI 交互的默认 Ssp。 在 Windows 操作系统中，使用 Ssp 以不同的方式来在不安全的网络环境中进行安全通信。

-   [Kerberos 安全支持提供程序](#BKMK_KerbSSP)

-   [NTLM 安全支持提供程序](#BKMK_NTLMSSP)

-   [摘要式安全支持提供程序](#BKMK_DigestSSP)

-   [Schannel 安全支持提供程序](#BKMK_SchannelSSP)

-   [协商安全支持提供程序](#BKMK_NegoSSP)

-   [凭据安全支持提供程序](#BKMK_CredSSP)

-   [协商扩展安全支持提供程序](#BKMK_NegoExtsSSP)

-   [PKU2U 安全支持提供程序](#BKMK_PKU2USSP)

本主题还包括：

[安全支持提供程序选择](security-support-provider-interface-architecture.md#BKMK_SecuritySupportProviderSelection)

### <a name="kerberos-security-support-provider"></a><a name="BKMK_KerbSSP"></a>Kerberos 安全支持提供程序
此 SSP 仅使用 Microsoft 实现的 Kerberos 版本5协议。 此协议基于网络工作组的 RFC 4120 和草稿版本。 它是一种行业标准协议，用于交互式登录的密码或智能卡。 它也是 Windows 中服务的首选身份验证方法。

由于从 Windows 2000 开始，Kerberos 协议是默认的身份验证协议，因此所有域服务都支持 Kerberos SSP。 这些服务包括：

-   Active Directory 使用轻型目录访问协议 (LDAP 的查询) 

-   使用远程过程调用服务的远程服务器或工作站管理

-   打印服务

-   客户端-服务器身份验证

-   使用服务器消息块 (SMB) 协议的远程文件访问 (也称为通用 Internet 文件系统或 CIFS) 

-   分布式文件系统管理和引用

-   Internet Information Services (IIS 的 Intranet 身份验证) 

-   Internet 协议安全 (IPsec) 的安全机构身份验证

-   用于域用户和计算机 Active Directory 证书服务的证书请求

位置：% windir% \Windows\System32\kerberos.dll

默认情况下，此提供程序包含在本主题开头的 " **应用于** " 列表中指定的版本中，以及 windows Server 2003 和 windows XP。

**Kerberos 协议和 Kerberos SSP 的其他资源**

-   [Microsoft Kerberos (Windows) ](/windows/win32/secauthn/microsoft-kerberos)

-   [\[KILE \] ： Kerberos 协议扩展](/openspecs/windows_protocols/ms-kile/2a32282e-dd48-4ad9-a542-609804b02cc9)

-   [\[MS-SFU \] ： Kerberos 协议扩展：用户服务和约束委派协议规范](/openspecs/windows_protocols/ms-sfu/3bff5864-8135-400e-bdd9-33b552051d94)

-   [Kerberos SSP/AP (Windows) ](/windows/win32/secauthn/kerberos-ssp-ap)

-   适用于 Windows Vista 的[Kerberos 增强功能](/previous-versions/windows/it-pro/windows-vista/cc749438(v=ws.10))

-   适用于 Windows 7 的[Kerberos 身份验证的更改](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560670(v=ws.10))

-   [Kerberos 身份验证技术参考](/previous-versions/windows/it-pro/windows-server-2003/cc739058(v=ws.10))

### <a name="ntlm-security-support-provider"></a><a name="BKMK_NTLMSSP"></a>NTLM 安全支持提供程序
Ntlm 安全支持提供程序 (NTLM SSP) 是安全支持提供程序接口使用的二进制消息传递协议 (SSPI) ，以允许 NTLM 质询响应身份验证，并协商完整性和机密性选项。 如果使用 SSPI 身份验证，则使用 NTLM，其中包括服务器消息块或 CIFS 身份验证、HTTP 协商身份验证 (例如，Internet Web Authentication) 和远程过程调用服务。 NTLM SSP 包含 NTLM 和 NTLM 版本 2 (NTLMv2) 身份验证协议。

受支持的 Windows 操作系统可将 NTLM SSP 用于以下内容：

-   客户端/服务器身份验证

-   打印服务

-   使用 CIFS (SMB) 进行文件访问

-   安全远程过程调用服务或 DCOM 服务

位置：% windir% \Windows\System32\msv1_0.dll

默认情况下，此提供程序包含在本主题开头的 " **应用于** " 列表中指定的版本中，以及 windows Server 2003 和 windows XP。

**NTLM 协议和 NTLM SSP 的其他资源**

-   [Windows) 的 MSV1_0 身份验证包 (](/windows/win32/secauthn/msv1-0-authentication-package)

-   Windows 7 中[NTLM 身份验证的更改](/previous-versions/windows/it-pro/windows-7/dd566199(v=ws.10))

-   [Microsoft NTLM (Windows)](/windows/win32/secauthn/microsoft-ntlm)

-   [审核和限制 NTLM 使用指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/jj865674(v=ws.10))

### <a name="digest-security-support-provider"></a><a name="BKMK_DigestSSP"></a>摘要式安全支持提供程序
摘要式身份验证是一种行业标准，用于轻型目录访问协议 (LDAP) 和 web 身份验证。 摘要式身份验证通过网络以 MD5 哈希或消息摘要形式传输凭据。

摘要式 SSP ( # A0) 用于以下内容：

-   Internet Explorer 和 Internet Information Services (IIS) 访问

-   LDAP 查询

位置：% windir% \Windows\System32\Digest.dll

默认情况下，此提供程序包含在本主题开头的 " **应用于** " 列表中指定的版本中，以及 windows Server 2003 和 windows XP。

**摘要式协议和摘要 SSP 的其他资源**

-   [ (Windows) Microsoft Digest 身份验证 ](/windows/win32/secauthn/microsoft-digest-ssp)

-   [\[DPSP \] ：摘要式协议扩展](/openspecs/windows_protocols/ms-dpsp/3e44be62-2067-472a-9ef0-e937298b68fb)

### <a name="schannel-security-support-provider"></a><a name="BKMK_SchannelSSP"></a>Schannel 安全支持提供程序
安全通道 (Schannel) 用于基于 web 的服务器身份验证，例如，当用户尝试访问安全 web 服务器时。

TLS 协议、SSL 协议、专用通信技术 (PCT) 协议、数据报传输层 (DTLS) 协议基于公钥加密。 Schannel 提供所有这些协议。 所有 Schannel 协议均使用客户端/服务器模型。 Schannel SSP 使用公钥证书验证参与方。 对参与方进行身份验证时，Schannel SSP 按以下优先顺序选择协议：

-   传输层安全性 (TLS) 版本1。0

-   传输层安全性 (TLS) 版本1。1

-   传输层安全性 (TLS) 版本1。2

-   安全套接字层 (SSL) 版本2。0

-   安全套接字层 (SSL) 版本3。0

-   专用通信技术 (PCT) 

    **注意** 默认情况下，PCT 处于禁用状态。

选择的协议是客户端和服务器可以支持的首选身份验证协议。 例如，如果服务器支持所有 Schannel 协议，而客户端仅支持 SSL 3.0 和 SSL 2.0，则身份验证过程使用 SSL 3.0。

当应用程序显式调用 DTLS 时使用。 有关 Schannel 提供程序使用的 DTLS 和其他协议的详细信息，请参阅 [Schannel 安全支持提供程序技术参考](../tls/schannel-security-support-provider-technical-reference.md)。

位置：% windir% \Windows\System32\Schannel.dll

默认情况下，此提供程序包含在本主题开头的 " **应用于** " 列表中指定的版本中，以及 windows Server 2003 和 windows XP。

> [!NOTE]
> 此提供程序在 Windows Server 2008 R2 和 Windows 7 中引入了 TLS 1.2。 Windows Server 2012 和 Windows 8 中的此提供程序中引入了 DTLS。

**TLS 和 SSL 协议以及 Schannel SSP 的其他资源**

-   [安全通道 (Windows) ](/windows/win32/secauthn/secure-channel)

-   [TLS/SSL 技术参考](/previous-versions/windows/it-pro/windows-server-2003/cc784149(v=ws.10))

-   [\[TLSP \] ： (TLS) 配置文件的传输层安全性](/openspecs/windows_protocols/ms-tlsp/58aba05b-62b0-4cd1-b88b-dc8a24920346)

### <a name="negotiate-security-support-provider"></a><a name="BKMK_NegoSSP"></a>协商安全支持提供程序
简单且受保护的 GSS-API 协商机制 (SPNEGO) 构成协商 SSP 的基础，whichcan 用于协商特定身份验证协议。 当某个应用程序调入 SSPI 以登录到网络时，该应用程序可以指定一个 SSP 来处理请求。 如果应用程序指定 Negotiate SSP，则它会分析请求，并根据客户配置的安全策略选择相应的提供程序来处理请求。

RFC 2478 中指定了 SPNEGO。

在支持的 Windows 操作系统版本中，协商安全支持提供程序在 Kerberos 协议和 NTLM 之间选择。 默认情况下，协商将选择 Kerberos 协议，除非该协议不能由身份验证中涉及的系统之一使用，或调用应用程序没有提供足够的信息来使用 Kerberos 协议。

位置：% windir% \Windows\System32\lsasrv.dll

默认情况下，此提供程序包含在本主题开头的 " **应用于** " 列表中指定的版本中，以及 windows Server 2003 和 windows XP。

**用于协商 SSP 的其他资源**

-   [Microsoft 协商 (Windows) ](/windows/win32/secauthn/microsoft-negotiate)

-   [\[SPNG \] ：简单且受保护的 GSS-API 协商机制 (SPNEGO) 扩展](/openspecs/windows_protocols/ms-spng/f377a379-c24f-4a0f-a3eb-0d835389e28a)

-   [\[N2HT \] ：协商和 NEGO2 HTTP 身份验证协议规范](/openspecs/windows_protocols/ms-n2ht/4b88aa77-4b12-4933-8740-0f32d8f4eacf)

### <a name="credential-security-support-provider"></a><a name="BKMK_CredSSP"></a>凭据安全支持提供程序
凭据安全服务提供程序 (CredSSP) 提供单一登录 (SSO) 用户在启动新终端服务和远程桌面服务会话时的体验。 CredSSP 使应用程序可以使用客户端 SSP) 通过服务器端 SSP)  (基于客户端策略的目标服务器，将用户的凭据从客户端计算机委托 (。 CredSSP 策略通过使用组策略进行配置，并且默认情况下禁用凭据的委派。

位置：% windir% \Windows\System32\credssp.dll

默认情况下，此提供程序包含在本主题开头的 " **适用** 于" 列表中指定的版本中。

**凭据 SSP 的其他资源**

-   [\[CSSP \] ：凭据安全支持提供程序 (CredSSP) 协议规范](/openspecs/windows_protocols/ms-cssp/85f57821-40bb-46aa-bfcb-ba9590b8fc30)

-   [用于终端服务登录的凭据安全服务提供程序和 SSO](/previous-versions/windows/it-pro/windows-vista/cc749211(v=ws.10))

### <a name="negotiate-extensions-security-support-provider"></a><a name="BKMK_NegoExtsSSP"></a>协商扩展安全支持提供程序
 (NegoExts) 的协商扩展是一种身份验证包，用于协商由 Microsoft 和其他软件公司实施的应用程序和方案使用的 Ssp （NTLM 或 Kerberos 协议除外）。

协商包的这一扩展允许以下方案：

-   **联合系统中丰富的客户端可用性。** 可以在 SharePoint 站点上访问文档，还可以使用功能完备的 Microsoft Office 应用程序对其进行编辑。

-   **为 Microsoft Office 服务提供丰富的客户端支持。** 用户可以登录到 Microsoft Office services 并使用全功能 Microsoft Office 应用程序。

-   **托管的 Microsoft Exchange 服务器和 Outlook。** 由于 Exchange Server 托管在 web 上，因此没有建立域信任。 Outlook 使用 Windows Live 服务对用户进行身份验证。

-   **客户端计算机和服务器之间的丰富客户端可用性。** 使用操作系统的网络和身份验证组件。

Windows 协商包与 NegoExts SSP 的处理方式与 Kerberos 和 NTLM 的处理方式相同。 在启动时，将 NegoExts.dll 加载到本地系统机构 (LSA) 。 当收到基于请求源的身份验证请求时，NegoExts 会在支持的 Ssp 之间进行协商。 它将收集凭据和策略，对其进行加密，并将该信息发送到创建安全令牌的相应 SSP。

NegoExts 支持的 Ssp 不是独立的 Ssp，如 Kerberos 和 NTLM。 因此，在 NegoExts SSP 内，如果出于任何原因而导致身份验证方法失败，则将显示或记录身份验证失败消息。 不能重新协商或回退身份验证方法。

位置：% windir% \Windows\System32\negoexts.dll

默认情况下，此提供程序包含在本主题开头的 " **适用于** " 列表中指定的版本中，不包括 windows Server 2008 和 windows Vista。

### <a name="pku2u-security-support-provider"></a><a name="BKMK_PKU2USSP"></a>PKU2U 安全支持提供程序
Windows 7 和 Windows Server 2008 R2 中引入了 PKU2U 协议，并将其作为 SSP 实现。 此 SSP 启用对等身份验证，特别是在 Windows 7 中引入了名为 "家庭组" 的媒体和文件共享功能。 此功能允许在非域成员的计算机之间共享。

位置：% windir% \Windows\System32\pku2u.dll

默认情况下，此提供程序包含在本主题开头的 " **适用于** " 列表中指定的版本中，不包括 windows Server 2008 和 windows Vista。

**PKU2U 协议和 PKU2U SSP 的其他资源**

-   [联机标识集成简介](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560662(v=ws.10))

## <a name="security-support-provider-selection"></a><a name="BKMK_SecuritySupportProviderSelection"></a>安全支持提供程序选择
Windows SSPI 可以使用通过安装的安全支持提供程序支持的任何协议。 但是，由于并非所有操作系统都支持与运行 Windows Server 的任何给定计算机相同的 SSP 包，因此，客户端和服务器必须协商使用两者都支持的协议。 Windows Server 倾向于客户端计算机和应用程序使用 Kerberos 协议，这是一种基于标准的强大协议，但操作系统继续允许不支持 Kerberos 协议进行身份验证的客户端计算机和客户端应用程序。

在进行身份验证之前，两台通信计算机必须同意它们都可以支持的协议。 对于任何可通过 SSPI 使用的协议，每台计算机都必须具有相应的 SSP。 例如，要使客户端计算机和服务器使用 Kerberos 身份验证协议，它们必须都支持 Kerberos v5。 Windows Server 使用函数 **EnumerateSecurityPackages** 来确定计算机上支持的 ssp 以及这些 ssp 的功能。

可以通过以下两种方式之一来处理身份验证协议的选择：

1.  [单个身份验证协议](#BKMK_SingleAuth)

2.  [Negotiate 选项](#BKMK_Negotiate)

### <a name="single-authentication-protocol"></a><a name="BKMK_SingleAuth"></a>单个身份验证协议
在服务器上指定一个可接受的协议时，客户端计算机必须支持指定的协议，否则通信将失败。 当指定了一个可接受的协议时，将按如下所示进行身份验证交换：

1.  客户端计算机请求对服务的访问权限。

2.  服务器会回复请求并指定要使用的协议。

3.  客户端计算机检查回复的内容并检查以确定它是否支持指定的协议。 如果客户端计算机确实支持指定的协议，则会继续进行身份验证。 如果客户端计算机不支持协议，则身份验证将失败，无论客户端计算机是否有权访问该资源。

### <a name="negotiate-option"></a><a name="BKMK_Negotiate"></a>Negotiate 选项
Negotiate 选项可用于允许客户端和服务器尝试查找可接受的协议。 这基于简单且受保护的 GSS-API 协商机制 (SPNEGO) 。 使用协商身份验证协议的选项开始身份验证时，SPNEGO 交换的发生方式如下：

1.  客户端计算机请求对服务的访问权限。

2.  服务器会根据第一次选择的协议，使用它可以支持的身份验证协议列表和身份验证质询或响应进行回复。 例如，服务器可能会列出 Kerberos 协议和 NTLM，并发送 Kerberos 身份验证响应。

3.  客户端计算机检查回复的内容并进行检查以确定它是否支持任何指定的协议。

    -   如果客户端计算机支持首选协议，则会继续进行身份验证。

    -   如果客户端计算机不支持首选协议，但它支持服务器列出的其他协议之一，则客户端计算机将使服务器知道它支持的身份验证协议，并且身份验证将继续。

    -   如果客户端计算机不支持任何列出的协议，则身份验证交换会失败。

## <a name="additional-references"></a>其他参考
[Windows 身份验证体系结构](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dn169024(v=ws.10))