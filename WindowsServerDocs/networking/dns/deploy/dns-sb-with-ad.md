---
title: 在 Active Directory 中使用针对拆分式 DNS 的 DNS 策略
description: 你可以使用本主题通过 Windows Server 2016 中的 Active Directory 集成的 DNS 区域，利用适用于裂脑部署的 DNS 策略的流量管理功能。
manager: brianlic
ms.topic: article
ms.assetid: f9533204-ad7e-4e49-81c1-559324a16aeb
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 1f6da8584f7a2b2221fb1a283b8ea4de842ddc58
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87964133"
---
# <a name="use-dns-policy-for-split-brain-dns-in-active-directory"></a>在 Active Directory 中使用针对拆分式 DNS 的 DNS 策略

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用本主题 \- 通过 Windows Server 2016 中的 Active Directory 集成的 dns 区域，利用用于 split 大脑部署的 dns 策略的流量管理功能。

在 Windows Server 2016 中，DNS 策略支持扩展到 Active Directory 集成的 DNS 区域。 Active Directory 集成 \- 为 DNS 服务器提供多主高可用性功能。

以前，此方案要求 DNS 管理员维护两个不同的 DNS 服务器，每个服务器为内部和外部用户提供服务。 如果区域中只拆分了几条记录 \- brained，或者 (内部和外部) 将区域的两个实例委托给相同的父域，这就成为了管理难题。

> [!NOTE]
> - \-当存在两个版本的单一区域、组织 intranet 上的内部用户的一个版本，以及一个适用于外部用户的版本（通常是 Internet 上的用户）时，DNS 部署会产生分裂。
> - 本主题[将 Dns 策略用于 Split 大脑 Dns 部署](split-brain-DNS-deployment.md)说明了如何使用 dns 策略和区域作用域 \- 在单个 WINDOWS server 2016 dns 服务器上部署裂脑 dns 系统。

## <a name="example-split-brain-dns-in-active-directory"></a>示例 \- 中的 Split 大脑 DNS Active Directory

此示例使用一家虚构公司 Contoso，该公司在 www.career.contoso.com 维护一个职业网站。

站点有两个版本，一个用于内部工作投递可用的内部用户。 此内部站点可在本地 IP 地址10.0.0.39 上找到。

第二个版本是同一站点的公共版本，可在公共 IP 地址65.55.39.10 获取。

在缺少 DNS 策略的情况下，管理员需要在单独的 Windows Server DNS 服务器上托管这两个区域，并单独对其进行管理。

使用 DNS 策略，现在可以在同一台 DNS 服务器上托管这些区域。

如果 contoso.com 的 DNS 服务器 Active Directory 集成，并且正在侦听两个网络接口，Contoso DNS 管理员可以按照本主题中的步骤来实现裂 \- 脑部署。

DNS 管理员配置具有以下 IP 地址的 DNS 服务器接口。

- 面向 Internet 的网络适配器使用公共 IP 地址208.84.0.53 为外部查询配置。
- 面向 Intranet 的网络适配器配置了专用 IP 地址10.0.0.56 用于内部查询。

下图描述了此方案。

![裂脑广告集成的 DNS 部署](../../media/DNS-SB-AD/DNS-SB-AD.jpg)

## <a name="how-dns-policy-for-split-brain-dns-in-active-directory-works"></a>\-Active Directory 中的 Split 大脑 dns 的 Dns 策略

当 DNS 服务器配置了所需的 DNS 策略时，将针对 DNS 服务器上的策略评估每个名称解析请求。

在此示例中，使用服务器接口来区分内部和外部客户端。

如果接收查询的服务器接口与任何策略匹配，则将使用关联的区域范围来响应查询。

因此，在我们的示例中，对专用 IP () 10.0.0.56 上收到的 www.career.contoso.com 的 DNS 查询将接收包含内部 IP 地址的 DNS 响应;在公共网络接口上接收的 DNS 查询接收包含默认区域作用域中的公共 IP 地址的 DNS 响应 (这与正常的查询解析) 相同。

\( \) 仅在默认区域作用域上支持动态 DNS DDNS 更新和清理。 由于内部客户端由默认区域作用域提供服务，Contoso DNS 管理员可以继续使用现有的机制 (动态 DNS 或静态) 来更新 contoso.com 中的记录。 对于非 \- 默认区域作用域 \( （如本示例中的外部范围 \) ），DDNS 或清理支持不可用。

### <a name="high-availability-of-policies"></a>策略的高可用性

DNS 策略不 Active Directory 集成。 因此，DNS 策略不会复制到托管相同 Active Directory 集成区域的其他 DNS 服务器。

DNS 策略存储在本地 DNS 服务器上。 使用以下示例 Windows PowerShell 命令，可以轻松地将 DNS 策略从一台服务器导出到另一台服务器。

```powershell
$policies = Get-DnsServerQueryResolutionPolicy -ZoneName "contoso.com" -ComputerName Server01
$policies |  Add-DnsServerQueryResolutionPolicy -ZoneName "contoso.com" -ComputerName Server02
```

有关详细信息，请参阅以下 Windows PowerShell 参考主题。

- [DnsServerQueryResolutionPolicy](https://docs.microsoft.com/powershell/module/dnsserver/get-dnsserverqueryresolutionpolicy?view=win10-ps)
- [DnsServerQueryResolutionPolicy](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps)

## <a name="how-to-configure-dns-policy-for-split-brain-dns-in-active-directory"></a>如何 \- 在 Active Directory 中配置 Split 大脑 dns 的 Dns 策略

若要使用 DNS 策略配置 DNS 拆分的部署，必须使用以下部分，其中提供了详细的配置说明。

### <a name="add-the-active-directory-integrated-zone"></a>添加 Active Directory 集成区域

你可以使用以下示例命令将 Active Directory 集成的 contoso.com 区域添加到 DNS 服务器。

```powershell
Add-DnsServerPrimaryZone -Name "contoso.com" -ReplicationScope "Domain" -PassThru
```

有关详细信息，请参阅[add-dnsserverprimaryzone](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverprimaryzone?view=win10-ps)。

### <a name="create-the-scopes-of-the-zone"></a>创建区域的作用域

您可以使用此部分对区域 contoso.com 进行分区，以创建外部区域作用域。

区域作用域是区域的唯一实例。 DNS 区域可以有多个区域作用域，每个区域作用域包含其自己的一组 DNS 记录。 同一条记录可以出现在多个作用域中，具有不同的 IP 地址或相同的 IP 地址。

因为你要将此新区域作用域添加到 Active Directory 集成区域中，所以区域范围和其中的记录将通过域中的其他副本服务器 Active Directory 进行复制。

默认情况下，区域作用域存在于每个 DNS 区域中。 此区域作用域具有与区域相同的名称，并且旧式 DNS 操作在此作用域上起作用。 此默认区域作用域将托管 www.career.contoso.com 的内部版本。

你可以使用以下示例命令在 DNS 服务器上创建区域作用域。

```powershell
Add-DnsServerZoneScope -ZoneName "contoso.com" -Name "external"
```

有关详细信息，请参阅[DnsServerZoneScope](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverzonescope?view=win10-ps)。

### <a name="add-records-to-the-zone-scopes"></a>将记录添加到区域作用域

下一步是将代表 web 服务器主机的记录添加到这两个区域作用域中-外部和默认 \( 的内部客户端 \) 。

在默认的内部区域范围内，将使用 IP 地址10.0.0.39 （即专用 IP 地址）添加记录 www.career.contoso.com;在外部区域作用域中，将 \( \) 随公共 IP 地址65.55.39.10 添加相同的记录 www.career.contoso.com。

\(默认内部区域作用域和外部区域作用域中的记录都 \) 将跨域自动复制到其各自的区域作用域。

你可以使用以下示例命令将记录添加到 DNS 服务器上的区域作用域。

```powershell
Add-DnsServerResourceRecord -ZoneName "contoso.com" -A -Name "www.career" -IPv4Address "65.55.39.10" -ZoneScope "external"
Add-DnsServerResourceRecord -ZoneName "contoso.com" -A -Name "www.career" -IPv4Address "10.0.0.39”
```

> [!NOTE]
> 将记录添加到默认区域作用域时，不包括 **– ZoneScope**参数。 此操作与将记录添加到普通区域相同。

有关详细信息，请参阅[DnsServerResourceRecord](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverresourcerecord?view=win10-ps)。

### <a name="create-the-dns-policies"></a>创建 DNS 策略

确定外部网络和内部网络的服务器接口并创建了区域作用域后，必须创建连接内部和外部区域作用域的 DNS 策略。

> [!NOTE]
> 此示例使用 \( 以下示例命令中的服务器接口-ServerInterface 参数 \) 作为条件来区分内部和外部客户端。 区分外部和内部客户端的另一种方法是使用客户端子网作为条件。 如果可以识别内部客户端所属的子网，则可以将 DNS 策略配置为基于客户端子网来区分。 有关如何使用客户端子网标准配置流量管理的信息，请参阅[将 DNS 策略用于基于地理位置的流量管理和主服务器](primary-geo-location.md)。

配置策略后，在公共接口上收到 DNS 查询时，会从区域的外部作用域返回答案。

> [!NOTE]
> 不需要任何策略即可映射默认的内部区域作用域。

```powershell
Add-DnsServerQueryResolutionPolicy -Name "SplitBrainZonePolicy" -Action ALLOW -ServerInterface "eq,208.84.0.53" -ZoneScope "external,1" -ZoneName contoso.com
```

> [!NOTE]
> 208.84.0.53 是公共网络接口上的 IP 地址。

有关详细信息，请参阅[DnsServerQueryResolutionPolicy](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps)。

现在 DNS 服务器使用 Active Directory 集成 DNS 区域的 split 大脑名称服务器的所需 DNS 策略进行配置。

你可以根据流量管理要求创建数千个 DNS 策略，并动态应用所有新策略，而无需重新启动 DNS 服务器的传入查询。
