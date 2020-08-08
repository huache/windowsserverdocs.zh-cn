---
title: 将 Active Directory 联合身份验证服务角色服务迁移到 Windows Server 2012 R2
description: 提供有关将 AD FS 服务迁移到 Windows Server 2012 R2 的说明。
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.openlocfilehash: 49c75fadcbc1284f23b490eb6ee48813ef40f781
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87970904"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012-r2"></a>将 Active Directory 联合身份验证服务角色服务迁移到 Windows Server 2012 R2
 本文档说明如何将以下角色服务迁移到随 Windows Server 2012 R2 一起安装的 Active Directory 联合身份验证服务 (AD FS) ：

-   Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合服务器

-   Windows Server 2012 上安装的 AD FS 联合服务器

## <a name="supported-migration-scenarios"></a>支持的迁移方案
 本指南中的迁移说明包括以下任务：

- 从运行 Windows Server 2008、Windows Server 2008 R2 或 Windows Server 2012 的服务器中导出 AD FS 2.0 配置数据

- 执行将此服务器的操作系统从 Windows Server 2008、Windows Server 2008 R2 或 Windows Server 2012 就地升级到 Windows Server 2012 R2 的操作。

- 在此服务器上重新创建原始 AD FS 配置并还原剩余的 AD FS 服务设置，该服务器现在正在运行随 Windows Server 2012 R2 一起安装的 AD FS 服务器角色。

  本指南不包括迁移运行多个角色的服务器的相关说明。 如果你的服务器正在运行多个角色，则建议你根据其他角色迁移指南中提供的信息，设计一个特定于你的服务器环境的自定义迁移过程。 [Windows Server 迁移门户](https://go.microsoft.com/fwlink/?LinkId=247608)中提供了适用于其他角色的迁移指南。

### <a name="supported-operating-systems"></a>支持的操作系统
 目标服务器操作系统：

 Windows Server 2012 R2 (Server Core 和完全安装选项) 

 目标服务器处理器：

 基于 x64

|源服务器处理器|源服务器操作系统|
|-----------------------------|------------------------------------|
|基于 x86 或基于 x64| Windows Server 2008，完全安装选项和服务器核心安装选项|
|基于 x64|Windows Server 2008 R2|
|基于 x64|Windows Server 2008 R2 的服务器核心安装选项|
|基于 x64|Windows Server 2012 的服务器核心和完全安装选项|

> [!NOTE]
> - 上表中列出的操作系统版本是所支持的操作系统和 Service Pack 的最旧组合。
>   -   支持将 Foundation、Standard、Enterprise 和 Datacenter 版本的 Windows Server 操作系统作为源服务器或目标服务器。
>   -   支持在物理操作系统和虚拟操作系统之间迁移。

### <a name="supported-ad-fs-role-services-and-features"></a>支持的 AD FS 角色服务和功能
 下表描述了本指南中介绍的 AD FS 角色服务迁移方案及其相关的设置。

|From|与 Windows Server 2012 R2 一起安装 AD FS|
|----------|----------------------------------------------------------------------------------------------|
|Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合服务器|支持在同一台服务器上迁移。 有关详细信息，请参阅：<p> [准备迁移 AD FS 联合服务器](prepare-migrate-ad-fs-server-r2.md)<p> [迁移 AD FS 联合服务器](migrate-ad-fs-fed-server-r2.md)|
|Windows Server 2012 上安装的 AD FS 联合服务器|支持在同一台服务器上迁移。  有关详细信息，请参阅：<p> [准备迁移 AD FS 联合服务器](prepare-migrate-ad-fs-server-r2.md)<p> [迁移 AD FS 联合服务器](migrate-ad-fs-fed-server-r2.md)|

## <a name="next-steps"></a>后续步骤
 [准备迁移 AD FS 联合服务器](prepare-migrate-ad-fs-server-r2.md)迁移[AD FS 联合](migrate-ad-fs-fed-server-r2.md)服务器迁移[AD FS 联合服务器代理](migrate-fed-server-proxy-r2.md)，[验证 AD FS 迁移到 Windows Server 2012 R2](verify-ad-fs-migration.md)