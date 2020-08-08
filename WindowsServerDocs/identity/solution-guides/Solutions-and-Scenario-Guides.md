---
ms.assetid: bdb9ad4b-139c-4031-8f26-827432779829
title: 解决方案和方案指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 6ed6f196d75797d25b6015d885d87a20868b9daa
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87940179"
---
# <a name="solutions-and-scenario-guides"></a>解决方案和方案指南

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012


利用 Microsoft 的访问和信息保护解决方案，你可以在本地环境和云应用程序中部署和配置对公司资源的访问。 你也可以在保护公司信息时执行此操作。

访问和信息保护

|指南|本指南如何帮助你
|-----|-----
| [在任何设备上从任何位置安全访问公司资源](/previous-versions/windows/it-pro/solutions-guidance/dn550982(v=ws.11))|本指南说明如何允许员工使用个人和公司设备安全访问公司应用程序和数据。
| [跨公司应用程序从任一设备加入工作区以实现 SSO 和无缝第二重身份验证](../ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications.md) | 员工可以在任何设备上随处访问应用程序和数据。 员工可以在浏览器应用程序或企业应用程序中使用单一登录。 管理员可以控制谁有权访问公司资源，而这些资源基于应用程序、用户、设备和位置。
| [使用适用于敏感应用程序的附加多重身份验证管理风险](../ad-fs/operations/manage-risk-with-additional-multi-factor-authentication-for-sensitive-applications.md)| 在此方案中，基于用户的组成员身份数据，对特定应用程序启用 MFA。 换而言之，你将在联合服务器上设置一个身份验证策略，要求属于特定组的用户请求访问 Web 服务器上托管的特定应用程序时使用 MFA。
| [使用条件访问控制管理风险](../ad-fs/operations/manage-risk-with-conditional-access-control.md) | AD FS 中的访问控制是使用颁发授权声明规则实施的，这些规则用于发出允许或拒绝声明，这些声明将确定是否允许某个用户或用户组访问 AD FS 保护的资源。 只能在信赖方信任上设置授权规则。
|[为自定义端口上的基于证书密钥的续订配置证书注册 Web 服务](certificate-enrollment-certificate-key-based-renewal.md)|本文提供了有关在443以外的自定义端口上实施证书注册 Web 服务 (或证书注册策略 (CEP) /证书注册 (服务的分步说明，用于基于证书密钥的续订，以利用 CEP 和 CES 的自动续订功能。 |
