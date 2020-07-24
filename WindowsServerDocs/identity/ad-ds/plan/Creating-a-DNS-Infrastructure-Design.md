---
ms.assetid: cd70b0aa-0a67-4966-a041-4dd3f302c98b
title: 创建 DNS 基础结构设计
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: c48996945e648a8ad698b1746e722702371521f1
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962349"
---
# <a name="creating-a-dns-infrastructure-design"></a>创建 DNS 基础结构设计

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

创建 Active Directory 林和域设计后，必须设计域名系统（DNS）基础结构来支持 Active Directory 逻辑结构。 DNS 使用户可以使用友好名称，这些名称易于在 IP 网络上连接到计算机和其他资源。 Windows Server 2008 中的 Active Directory 域服务（AD DS）需要 DNS。

根据你的组织是否已有 DNS 服务器服务或正在部署新的 DNS 服务器服务，设计 DNS 以支持 AD DS 的过程会有所不同：

- 如果你已有现有的 DNS 基础结构，则必须将 Active Directory 命名空间集成到该环境中。 有关详细信息，请参阅[将 AD DS 集成到现有的 DNS 基础结构](../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md)。
- 如果没有现成的 DNS 基础结构，则必须设计和部署新的 DNS 基础结构来支持 AD DS。 有关详细信息，请参阅[部署域名系统（DNS）](/previous-versions/windows/it-pro/windows-server-2003/cc780661(v=ws.10))。

如果你的组织具有现有的 DNS 基础结构，则必须确保了解你的 DNS 基础结构将如何与 Active Directory 命名空间进行交互。 要使工作表可以帮助你记录现有 DNS 基础结构的设计，请从[Windows Server 2003 部署工具包的作业帮助](https://microsoft.com/download/details.aspx?id=9608)下载 Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip，并打开 "DNS 清单" （DSSLOGI_8.doc）。

> [!NOTE]
> 除了 IP 版本4（IPv4）地址以外，Windows Server 还支持 IP 版本6（IPv6）地址。 要使工作表在记录当前 DNS 结构的递归名称解析方法时帮助你列出 IPv6 地址，请参阅[附录 a： DNS 清单](../../ad-ds/plan/Appendix-A--DNS-Inventory.md)。

在设计 DNS 基础结构以支持 AD DS 之前，请阅读有关 DNS 层次结构、DNS 名称解析过程以及 DNS 如何支持 AD DS 的信息。 有关 DNS 层次结构和名称解析过程的详细信息，请参阅[Dns 技术参考](/previous-versions/windows/it-pro/windows-server-2003/cc779926(v=ws.10))。 有关 DNS 如何支持 AD DS 的详细信息，请参阅[Active Directory 技术参考的 Dns 支持](/previous-versions/windows/it-pro/windows-server-2003/cc781627(v=ws.10))。

## <a name="in-this-section"></a>本节内容

- [查看 DNS 概念](../../ad-ds/plan/Reviewing-DNS-Concepts.md)
- [DNS 和 AD DS](../../ad-ds/plan/DNS-and-AD-DS.md)
- [为 AD DS 所有者角色分配 DNS](../../ad-ds/deploy/Assigning-the-DNS-for-AD-DS-Owner-Role.md)
- [将 AD DS 集成到现有的 DNS 基础结构](../../ad-ds/plan/../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md)
