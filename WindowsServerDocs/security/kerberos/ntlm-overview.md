---
title: NTLM Overview
description: Windows Server 安全
ms.topic: article
ms.assetid: 773909fd-c0bc-498a-95fc-bb452ec04d90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: b81d59a350f5549cdb83af7299b8636fb917cc24
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87996083"
---
# <a name="ntlm-overview"></a>NTLM Overview

>适用于：Windows Server（半年频道）、Windows Server 2016

适用于 IT 专业人员的本主题介绍 NTLM、功能的任何更改，并提供指向 Windows 身份验证的技术资源的链接以及 Windows Server 2012 和早期版本的 NTLM。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能说明
NTLM 身份验证是 Windows Msv10.dll 中包含的一系列身份验证协议 \_ 。 NTLM 身份验证协议包括 LAN Manager 版本 1 和 2 以及 NTLM 版本 1 和 2。 NTLM 身份验证协议基于一种质询响应机制对用户和计算机进行身份验证， \/ 该机制向服务器或域控制器证明用户知道与帐户关联的密码。 在使用 NTLM 协议时，每当需要新的访问令牌时，资源服务器必须执行以下操作之一来验证计算机或用户的身份：

-   如果计算机或用户的帐户是域帐户，请联系域控制器的部门域认证服务来获取该帐户的域。

-   如果该计算机或用户的帐户是本地帐户，请在本地帐户数据库中查找该帐户。

## <a name="current-applications"></a><a name="BKMK_APP"></a>当前应用程序
NTLM 身份验证仍受支持，必须用于系统配置为工作组成员的 Windows 身份验证。 NTLM 身份验证还可用于非域控制器上的本地登录身份验证 \- 。 Kerberos 版本5身份验证是 Active Directory 环境的首选身份验证方法，但非 \- microsoft 或 Microsoft 应用程序仍可以使用 NTLM。

在 IT 环境中减少 NTLM 协议的使用需要了解 NTLM 上的部署应用程序要求，以及配置计算环境以使用其他协议所需的策略和步骤。 添加了新工具和设置以帮助你了解如何使用 NTLM 以便有选择地限制 NTLM 流量。 有关如何在你的环境中分析和限制 NTLM 使用的信息，请参阅 [NTLM 身份验证限制简介](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560653(v=ws.10)) 以访问审核和限制 NTLM 使用指南。

## <a name="new-and-changed-functionality"></a><a name="BKMK_NEW"></a>新功能和更改的功能
对于适用于 Windows Server 2012 的 NTLM，没有任何功能更改。

## <a name="removed-or-deprecated-functionality"></a><a name="BKMK_DEP"></a>已删除或弃用的功能
适用于 Windows Server 2012 的 NTLM 没有已删除或弃用的功能。

## <a name="server-manager-information"></a><a name="BKMK_INSTALL"></a>服务器管理器信息
NTLM 无法从服务器管理器进行配置。 你可以使用安全策略设置或组策略管理计算机系统之间的 NTLM 身份验证使用。 在域中，Kerberos 是默认身份验证协议。

## <a name="see-also"></a><a name="BKMK_LINKS"></a>另请参阅
下表列出了 NTLM 和其他 Windows 身份验证技术的相关资源。

|内容类型|参考|
|--------|-------|
|**产品评估**|[NTLM 身份验证限制简介](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560653(v=ws.10))<p>[NTLM 身份验证的更改](/previous-versions/windows/it-pro/windows-7/dd566199(v=ws.10))|
|规划|[IT 基础结构威胁建模指南](/previous-versions/tn-archive/dd941826(v=technet.10))<p>[威胁和对策：Windows Server 2003 和 Windows XP 中的安全设置](/previous-versions/tn-archive/dd162275(v=technet.10))<p>[威胁和对策指南：Windows Server 2008 和 Windows Vista 中的安全设置](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd349791(v=ws.10))<p>[威胁和对策指南：Windows Server 2008 R2 和 Windows 7 中的安全设置](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh125921(v=ws.10))|
|**部署**|[身份验证的扩展保护](https://support.microsoft.com/kb/968389)<p>[审核和限制 NTLM 使用指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/jj865674(v=ws.10))<p>[询问目录服务团队：NTLM 阻止和你：Windows 7 中的应用程序分析和审核方法](https://blogs.technet.com/askds/archive/2009/10/08/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7.aspx)<p>[Windows 身份验证博客](https://blogs.technet.com/authentication/)<p>[为 NTLM 传递身份验证配置 MaxConcurrentAPI](https://support.microsoft.com/help/2688798/how-to-do-performance-tuning-for-ntlm-authentication-by-using-the-maxc)|
|**开发**|[Microsoft NTLM \( Windows\)](/windows/win32/secauthn/microsoft-ntlm)<p>[\[MS \- NLMP \] ： NT LAN 管理器 \( NTLM \) 身份验证协议规范](https://msdn.microsoft.com/library/cc236621(PROT.10).aspx)<p>[\[MS \- NNTP \] ： NT LAN Manager \( NTLM \) 身份验证：网络新闻传输协议 \( NNTP \) 扩展](https://msdn.microsoft.com/library/cc236774(PROT.10).aspx)<p>[\[MS \- NTHT \] ： NTLM Over HTTP 协议规范](https://msdn.microsoft.com/library/cc237488(PROT.10).aspx)|
|**故障排除**|目前不可用|
|**社区资源**|[“NTLM 瓶颈和 RPC运行时”还有生命力吗？](https://blogs.technet.com/b/askds/archive/2011/09/15/is-this-horse-dead-yet-ntlm-bottlenecks-and-the-rpc-runtime.aspx)|