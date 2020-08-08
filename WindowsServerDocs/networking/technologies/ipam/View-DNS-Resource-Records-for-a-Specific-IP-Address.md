---
title: 查看用于特定 IP 地址的 DNS 资源记录
description: 本主题是 Windows Server 2016 中的 IP 地址管理 (IPAM) 管理指南的一部分。
manager: brianlic
ms.topic: article
ms.assetid: f590fb86-4195-4f90-98cb-e90459d4c1e3
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 211dcfdc17cfa81aad7adb1a424a9fadc0c932c6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87944598"
---
# <a name="view-dns-resource-records-for-a-specific-ip-address"></a>查看用于特定 IP 地址的 DNS 资源记录

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用本主题来查看与所选 IP 地址关联的 DNS 资源记录。

Administrators**** 组成员或同等身份是执行此过程的最低要求。

### <a name="to-view-resource-records-for-an-ip-address"></a>查看 IP 地址的资源记录

1.  在服务器管理器中，单击 " **IPAM**"。 IPAM 客户端控制台随即出现。

2.  在导航窗格中的 " **IP 地址空间**" 中，单击 " **ip 地址清单**"。 在下部导航窗格中，单击 " **IPv4** " 或 " **IPv6**"。 IP 地址清单显示在显示窗格搜索视图中。 找到并选择要查看其 DNS 资源记录的 IP 地址。

    ![查看 IP 地址清单](../../media/View-DNS-Resource-Records-for-a-Specific-IP-Address/ipam_IPInventory_01.jpg)

3.  在显示窗格**详细信息视图**中，单击 " **DNS 资源记录**"。 将显示与所选 IP 地址关联的资源记录。

    ![查看 DNS 资源记录](../../media/View-DNS-Resource-Records-for-a-Specific-IP-Address/ipam_IPInventory_02.jpg)

## <a name="see-also"></a>另请参阅
[DNS 资源记录管理](DNS-Resource-Record-Management.md) 
[管理 IPAM](Manage-IPAM.md)



