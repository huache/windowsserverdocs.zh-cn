---
ms.assetid: 39c0126d-af5e-4dcb-88c1-aa38f888e973
title: Active Directory 集成 DNS 区域
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 4f313b09954697f4b54c31a1721311ea0a017dd5
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941267"
---
# <a name="active-directory-integrated-dns-zones"></a>Active Directory 集成 DNS 区域

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

域名系统 (DNS) 域控制器上运行的服务器可以将其区域存储在 Active Directory 域服务 (AD DS) 。 通过这种方式，不必配置单独的 DNS 复制拓扑，该拓扑使用普通的 DNS 区域传输，因为所有区域数据都是通过 Active Directory 复制方式自动复制的。 这简化了部署 DNS 的过程，并提供了以下优势：

- 为 DNS 复制创建了多个主机。 因此，运行 DNS 服务器服务的域中的任何域控制器都可以将更新写入到 Active Directory 集成的 DNS 区域，以供其获得权威的域名。 不需要单独的 DNS 区域传送拓扑。

- 支持安全动态更新。 安全动态更新允许管理员控制哪些计算机更新哪些名称并防止未经授权的计算机覆盖 DNS 中的现有名称。

Windows Server 2008 中 Active Directory 集成的 DNS 将区域数据存储在应用程序目录分区中。  (基于 Windows Server 2003 的 DNS 与 Active Directory 的集成中没有行为更改。 ) 以下特定于 DNS 的应用程序目录分区是在 AD DS 安装期间创建的：

- 林范围的应用程序目录分区，称为 ForestDnsZones

- 林中每个域的域范围的应用程序目录分区，名为 DomainDnsZones

有关 AD DS 如何在应用程序分区中存储 DNS 信息的详细信息，请参阅 [Dns 技术参考](/previous-versions/windows/it-pro/windows-server-2003/cc779926(v=ws.10))。

> [!NOTE]
> 建议你在运行 Active Directory 域服务安装向导 ( # A0) 时安装 DNS。 如果这样做，该向导将自动创建 DNS 区域委派。 有关详细信息，请参阅 [部署 Windows Server 2008 林根级域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174(v=ws.10))。
