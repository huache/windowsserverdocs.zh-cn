---
title: 迁移 AD FS 2.0 联合代理服务器
description: 提供有关将 AD FS 代理服务器迁移到 Windows Server 2012 R2 的信息。
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.openlocfilehash: a8345f587e7fe4119e46dc390e9240dee6071ce6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87940830"
---
# <a name="migrate-the-active-directory-federation-services-proxy-server-to-windows-server-2012-r2"></a>将 Active Directory 联合身份验证服务代理服务器迁移到 Windows Server 2012 R2

在 Windows Server 2012 R2 的 Active Directory 联合身份验证服务 (AD FS) 中，联合服务器代理的角色由称为 Web 应用程序代理的新远程访问角色服务处理。 在 Windows Server 2012 R2 中，若要使您的 AD FS 可以从企业网络外部进行访问，您可以部署一个或多个 Web 应用程序代理。 但是，不能将在 Windows Server 2008 R2 或 Windows Server 2012 上运行的联合服务器代理迁移到在 Windows Server 2012 R2 上运行的 Web 应用程序代理。

> [!IMPORTANT]
>  不支持将在 Windows Server 2008、Windows Server 2008 R2 或 Windows Server 2012 上运行的联合服务器代理迁移到在 Windows 2012 Server 上运行的 Web 应用程序代理。

如果要在 Windows Server 2012 R2 迁移场中配置 AD FS 以进行 extranet 访问，则必须在 AD FS 基础结构中执行一个或多个 Web 应用程序代理计算机的全新部署。

若要规划 Web 应用程序代理部署，可以查看以下主题中的信息：

- [规划 Web 应用程序代理基础结构](/previous-versions/orphan-topics/ws.11/dn383648(v=ws.11))

- [规划 Web 应用程序代理服务器](/previous-versions/orphan-topics/ws.11/dn383647(v=ws.11))

  若要部署 Web 应用程序代理，可以遵循以下主题中的过程：

- [配置 Web 应用程序代理基础结构](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383644(v=ws.11))

- [安装和配置 Web 应用程序代理服务器](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383662(v=ws.11))

## <a name="next-steps"></a>后续步骤
 [将 Active Directory 联合身份验证服务角色服务迁移到 Windows server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md) [正在准备迁移 AD FS 联合服务器](prepare-migrate-ad-fs-server-r2.md)[迁移 AD FS 联合服务器](migrate-ad-fs-fed-server-r2.md)将[验证 AD FS 迁移到 windows server 2012 r2](verify-ad-fs-migration.md)
