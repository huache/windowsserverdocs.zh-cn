---
ms.assetid: 4163cf03-3bff-426c-9844-4cc2d7897d52
title: 为 AD DS 所有者角色分配 DNS
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: e0b4d51014173c8ae33b29452f59fa96ab7538b1
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87959165"
---
# <a name="assigning-the-dns-for-ad-ds-owner-role"></a>为 AD DS 所有者角色分配 DNS

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

林所有者为林的 Active Directory 域服务 (AD DS) 所有者分配域名系统 (DNS) 。 林的 AD DS 所有者 (或一组人员) 负责监视 DNS 的部署 AD DS 基础结构，并确保在必要的情况 (使用正确的 Internet 机构注册域名时使用。

AD DS 所有者的 DNS 负责为林 AD DS 设计的 DNS。 如果你的组织当前正在运行 DNS 服务器服务，则现有 DNS 服务器服务的 DNS 设计器将与 DNS AD DS 所有者合作，以将林根 DNS 名称委派到域控制器上运行的 DNS 服务器。

林的 DNS AD DS 所有者还会与动态主机配置协议 (DHCP) 组和组织的 DNS 组联系，并协调林中每个域的单个 DNS 所有者的计划 (如果有这些组的任何) 。 林的 DNS 所有者确保 DNS 中的 DHCP 和 DNS 组都参与 AD DS 的设计过程中，以便每个组都知道 DNS 设计计划，并可以及早提供输入。



