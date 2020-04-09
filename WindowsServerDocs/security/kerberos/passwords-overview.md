---
title: 密码概述
description: Windows Server 安全
ms.prod: windows-server
ms.technology: security-kerberos
ms.topic: article
ms.assetid: f608960e-2039-4c91-9c8c-9b81053c675e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 19003d5dcfdaa0f9d6dafcc31bab31a5cb50efa0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858830"
---
# <a name="passwords-overview"></a>密码概述

>适用于：Windows Server（半年频道）、Windows Server 2016

适用于 IT 专业人员的本主题介绍了 Windows 操作系统中使用的密码，并链接到有关凭据管理策略中的密码使用的文档和讨论。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能描述
如今的操作系统和应用程序都是围绕密码来构建的，即使使用智能卡或生物识别系统，所有帐户仍具有密码，但在某些情况下仍然可以使用这些帐户。 某些帐户（特别是用于运行服务的帐户）甚至不能使用智能卡和生物识别令牌，因此必须使用密码进行身份验证。 Windows 使用加密哈希来保护密码。

有关 Windows 密码的详细信息，请参阅[密码技术概述](https://technet.microsoft.com/library/hh994558(WS.10).aspx)。

## <a name="practical-applications"></a><a name="BKMK_APP"></a>实用应用程序
在 Windows 和许多其他操作系统中，对用户标识进行身份验证的最常见方法是使用机密通行短语或密码。 保护网络环境要求所有用户都使用强密码。 这有助于避免恶意用户猜测弱密码的威胁，无论是通过手动方法还是通过使用工具获取已泄露的用户帐户的凭据。 对于管理帐户尤其如此。 如果定期更改复杂的密码，则会减少密码攻击损害该帐户的可能性。

## <a name="new-and-changed-functionality"></a><a name="BKMK_NEW"></a>新增功能和更改的功能
在 Windows Server 2012 和 Windows 8 中，图片密码是新的。 图片密码是用户选择的图像与一系列手势耦合的组合。 已加入域\-已加入计算机上的图片密码功能被禁用。 有关图片密码的详细信息的链接，请参阅下面的 "[另请参阅](#BKMK_LINKS)"。

Windows Server 2012 和 Windows 8 中没有密码功能更改。 尚未添加新的组策略设置。 但是，凭据 \(和密码\) 管理中已进行了改进和增强，如使用图片密码、凭据保险箱和使用 Microsoft 帐户登录 Windows 8 （以前称为 Windows Live ID）。

## <a name="deprecated-functionality"></a><a name="BKMK_DEP"></a>弃用的功能
Windows Server 2012 和 Windows 8 中未弃用密码功能。

## <a name="software-requirements"></a><a name="BKMK_SOFT"></a>软件要求
在企业环境中，密码通常用 Active Directory 域服务进行管理。 还可以使用 "本地安全设置"、"帐户策略" 和 "密码策略" 中的设置在本地计算机上管理密码。

## <a name="see-also"></a><a name="BKMK_LINKS"></a>另请参阅
此表列出了密码功能、技术和凭据管理的其他资源。

|内容类型|参考|
|--------|-------|
|**方案文档**|[保护数字标识](https://blogs.msdn.com/b/b8/archive/2011/12/14/protecting-your-digital-identity.aspx)|
|**操作**|[Active Directory 用户和计算机](https://technet.microsoft.com/library/cc754217.aspx)|
|**疑难解答**|[查看密码过期时间 \- Active Directory PowerShell 博客](https://blogs.msdn.com/b/adpowershell/archive/2010/08/09/9970198.aspx)|
|**安全性**| Windows Server 2008 R2 和 Windows 7[威胁和对策指南：帐户策略](https://technet.microsoft.com/library/hh125920(v=ws.10).aspx)<p>[更改和创建强密码](https://www.microsoft.com/security/online-privacy/passwords-create.aspx)的指南|
|**工具和设置**|[Microsoft 下载中心上的 Windows 和 Windows Server 组策略设置参考](https://www.microsoft.com/download/en/details.aspx?amp;displaylang=en&displaylang=en&id=25250)|
|**社区资源**|[保护数字标识](https://blogs.msdn.com/b/b8/archive/2011/12/14/protecting-your-digital-identity.aspx)<p>[使用 Windows Live ID 登录 Windows 8](https://blogs.msdn.com/b/b8/archive/2011/09/26/signing-in-to-windows-8-with-a-windows-live-id.aspx)<p>[使用图片密码登录](https://blogs.msdn.com/b/b8/archive/2011/12/16/signing-in-with-a-picture-password.aspx)<p>[优化图片密码安全性](https://blogs.msdn.com/b/b8/archive/2011/12/19/optimizing-picture-password-security.aspx)|


