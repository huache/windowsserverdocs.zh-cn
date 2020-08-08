---
title: 配置 AD FS 禁止的 IP 地址
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.openlocfilehash: e5cb939fcf862d16837c2f9e05548644faf3bf71
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956484"
---
# <a name="ad-fs-and-banned-ip-addresses"></a>AD FS 和禁止的 IP 地址


2018年6月，Windows Server 2016 上的 AD FS 引入了 AD FS 6 月2018更新的**禁止 ip** 。  此更新使你能够在 AD FS 中全局配置一组 IP 地址，以便从这些 IP 地址传入的请求，或在**x-转发**的或**x 毫秒转发的客户端 ip**标头中包含这些 ip 地址的请求将被 AD FS 阻止。

## <a name="adding-banned-ips"></a>添加禁止的 Ip
若要将禁止的 Ip 添加到全局列表，请使用以下 Powershell cmdlet：

``` powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

允许的格式

1.  IPv4
2.  IPv6
3.  具有 IPv4 或 v6 的 CIDR 格式

对于禁止的 IP 地址，限制为300个条目。 您可以使用 CIDR 或范围格式拒绝带有单个条目的大型条目块。

## <a name="removing-banned-ips"></a>删除禁止的 Ip
若要从全局列表中删除禁止的 Ip，请使用以下 Powershell cmdlet：

``` powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

#### <a name="read-banned-ips"></a>读取禁止的 Ip
若要读取当前的一组禁止的 IP 地址，请使用以下 Powershell cmdlet：

``` powershell
PS C:\ >Get-AdfsProperties
```

示例输出：

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>其他参考
[保护 Active Directory 联合身份验证服务的最佳实践](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-adfsproperties](/powershell/module/adfs/set-adfsproperties?view=win10-ps)

[AD FS 操作](../ad-fs-operations.md)
