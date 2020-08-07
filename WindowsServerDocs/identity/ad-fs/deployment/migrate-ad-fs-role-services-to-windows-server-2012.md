---
title: 将 Active Directory 联合身份验证服务角色服务迁移到 Windows Server 2012
description: 提供有关将 AD FS 服务迁移到 Windows Server 2012 的说明。
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.openlocfilehash: abbd51daea374eb4684f5416bed45fb0aaf315d4
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938207"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012"></a>将 Active Directory 联合身份验证服务角色服务迁移到 Windows Server 2012

下面提供有关将以下角色服务迁移到 Windows Server 2012 上的 Active Directory 联合身份验证服务 (AD FS) 的说明：

-   随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 基于 Windows 令牌的代理和 AD FS 1.1 声明感知代理

-   在 Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合服务器和 AD FS 2.0 联合服务器代理

## <a name="supported-migration-scenarios"></a>支持的迁移方案
 迁移说明包括以下任务：

- 从运行 Windows Server 2008 或 Windows Server 2008 R2 的服务器导出 AD FS 2.0 配置数据

- 执行将此服务器的操作系统从 Windows Server 2008 或 Windows Server 2008 R2 就地升级到 Windows Server 2012 的操作。

- 在此服务器上重新创建原始 AD FS 配置并还原剩余的 AD FS 服务设置，该服务器现在正在运行随 Windows Server 2012 一起安装的 AD FS 服务器角色。

  本指南不包括迁移运行多个角色的服务器的相关说明。 如果你的服务器正在运行多个角色，则建议你根据其他角色迁移指南中提供的信息，设计一个特定于你的服务器环境的自定义迁移过程。 [Windows Server 迁移门户](https://go.microsoft.com/fwlink/?LinkId=247608)中提供了适用于其他角色的迁移指南。

## <a name="supported-operating-systems"></a>支持的操作系统
 **目标服务器操作系统：**


- Windows Server 2012 或 Windows Server 2008 R2 (Server Core 和完全安装选项) 

  **目标服务器处理器：**


- 基于 x64

|源服务器处理器|源服务器操作系统|
|-----|-----|
|基于 x86 或基于 x64|带 Service Pack 2 的 Windows Server 2003|
|基于 x86 或基于 x64|Windows Server 2003 R2|
|基于 x86 或基于 x64|Windows Server 2008，完全安装选项和服务器核心安装选项|
|基于 x64|Windows Server 2008 R2|
|基于 x64|Windows Server 2008 R2 的服务器核心安装选项|
|基于 x64|Windows Server 2012 的服务器核心和完全安装选项|

> [!NOTE]
> - 上表中列出的操作系统版本是所支持的操作系统和 Service Pack 的最旧组合。
>   -   支持将 Foundation、Standard、Enterprise 和 Datacenter 版本的 Windows Server 操作系统作为源服务器或目标服务器。
>   -   支持在物理操作系统和虚拟操作系统之间迁移。

### <a name="supported-ad-fs-role-services-and-features"></a>支持的 AD FS 角色服务和功能
 下表描述了本指南中介绍的 AD FS 角色服务迁移方案及其相关的设置。

|From|与 Windows Server 2012 一起安装 AD FS|
|----------|-----|
|随 Windows Server 2003 R2 一起安装的 AD FS 1.0 联合服务器|不支持迁移|
|随 Windows Server 2003 R2 一起安装的 AD FS 1.0 联合服务器代理|不支持迁移|
|随 Windows Server 2003 R2 一起安装的 AD FS 1.0 基于 Windows 令牌的代理|不支持迁移|
|随 Windows Server 2003 R2 一起安装的 AD FS 1.0 声明感知代理|不支持迁移|
|随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 联合服务器|不支持迁移|
|随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 联合服务器代理|不支持迁移|
|随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 基于 Windows 令牌的代理|支持在同一服务器上的迁移，但所迁移的 AD FS 基于 Windows 令牌的代理仅在随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 联合身份验证服务下运行。 有关详细信息，请参阅：<p> [迁移 AD FS 1.1 Web 代理](migrate-the-ad-fs-web-agent.md)<p> [与 AD FS 1.x 进行互操作](Interoperating-with-AD-FS-1.x.md)|
|随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 声明感知代理|支持在同一台服务器上迁移。 迁移的 AD FS 1.1 声明感知 Web 代理将与以下内容一起运行：<p> 随 Windows Server 2008 或 Windows Server 2008 R2 一起安装的 AD FS 1.1 联合身份验证服务<p> Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合身份验证服务<p> 随 Windows Server 2012 一起安装 AD FS 联合身份验证服务<p> 有关详细信息，请参阅：<p> [迁移 AD FS 1.1 Web 代理](migrate-the-ad-fs-web-agent.md)<p> [与 AD FS 1.x 进行互操作](Interoperating-with-AD-FS-1.x.md)|
|Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合服务器|支持在同一台服务器上迁移。 有关详细信息，请参阅：<p> [准备迁移 AD FS 2.0 联合服务器](prepare-to-migrate-ad-fs-fed-server.md)<p> [迁移 AD FS 2.0 联合服务器](migrate-the-ad-fs-fed-server.md)|
|在 Windows Server 2008 或 Windows Server 2008 R2 上安装的 AD FS 2.0 联合服务器代理|支持在同一台服务器上迁移。  有关详细信息，请参阅：<p> [准备迁移 AD FS 2.0 联合服务器代理](prepare-to-migrate-ad-fs-fed-proxy.md)<p> [迁移 AD FS 2.0 联合服务器代理](migrate-the-ad-fs-2-fed-server-proxy.md)|

## <a name="see-also"></a>另请参阅
 [准备迁移 AD FS 2.0 联合服务器](prepare-to-migrate-ad-fs-fed-server.md)[准备迁移 AD FS 2.0 联合服务器代理](prepare-to-migrate-ad-fs-fed-proxy.md)[迁移 AD FS 2.0 联合服务器](migrate-the-ad-fs-fed-server.md)迁移[AD FS 2.0 联合服务器代理](migrate-the-ad-fs-2-fed-server-proxy.md)[迁移 AD FS 1.1 Web 代理](migrate-the-ad-fs-web-agent.md)