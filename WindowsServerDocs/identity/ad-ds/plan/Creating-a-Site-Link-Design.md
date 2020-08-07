---
ms.assetid: 206b8072-1d0c-4a0b-ba8a-35a868d67b4c
title: 创建站点链接设计
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.openlocfilehash: f10fea4e6e94ecc6636fe13588fea2bb94ad4407
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87947759"
---
# <a name="creating-a-site-link-design"></a>创建站点链接设计

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

创建站点链接设计以使用站点链接来连接站点。 站点链接反映了用于传输复制流量的站点间连接和方法。 必须将站点与站点链接相连接，以便每个站点的域控制器可以复制 Active Directory 更改。

## <a name="connecting-sites-with-site-links"></a>将站点与站点链接相连接

若要将站点与站点链接相连接，请使用站点链接标识要连接的成员站点，在各自的站点间传输容器中创建站点链接对象，然后命名该站点链接。 创建站点链接后，可以继续设置站点链接属性。

创建站点链接时，请确保每个站点都包括在站点链接中。 此外，请确保所有站点通过其他站点链接彼此连接，以便可以将更改从任何站点中的域控制器复制到所有其他站点。 如果无法执行此操作，则会在目录服务日志中生成一条错误消息，事件查看器表明站点拓扑未连接。

每次将站点添加到新创建的站点链接时，确定要添加的站点是否为其他站点链接的成员，并根据需要更改站点的站点链接成员身份。 例如，如果你在最初创建站点时使站点成为默认的第一个站点链接的成员，则在将站点添加到新站点链接之后，请确保从默认的第一个站点链接中删除该站点。 如果未从默认的第一个站点链接中删除该站点，则 (KCC) 的知识一致性检查器将根据这两个站点链接的成员身份来做出路由决策，这可能会导致路由不正确。

若要确定要使用站点链接连接的成员站点，请使用在 "地理位置和通信链接" ( # A0) 工作表中记录的位置和链接位置的列表。 如果多个站点具有相同的连接和可用性，则可以使用同一站点链接连接它们。

站点间传输容器提供将站点链接映射到链接使用的传输的方法。 当你创建站点链接对象时，你可以在 IP 容器中创建它，该容器将站点链接与远程过程调用关联 (RPC) 通过 IP 传输，或使用简单邮件传输协议 (SMTP) 容器，后者将站点链接与 SMTP 传输相关联。

> [!NOTE]
> Active Directory 域服务 (AD DS 的未来版本中将不支持 SMTP 复制) ;因此，不建议在 SMTP 容器中创建站点链接对象。

当你在各自的站点间传输容器中创建站点链接对象时，AD DS 会通过 IP 使用 RPC 在域控制器之间传输站点间和站点内复制。 为了在传输过程中保护数据的安全，通过 IP 的 RPC 复制同时使用 Kerberos 身份验证协议和数据加密。

当直接 IP 连接不可用时，你可以配置站点之间的复制以使用 SMTP。 不过，SMTP 复制功能受到限制，并且需要 (CA) 的企业证书颁发机构。 SMTP 只能复制配置、架构和应用程序目录分区，并且不支持域目录分区的复制。

若要命名站点链接，请使用一致的命名方案，如 name_of_site1 name_of_site2。 记录站点列表、链接站点，以及在工作表中连接这些站点的站点链接的名称。 要使工作表可以帮助你记录站点名称和关联的站点链接名称，请参阅[Windows Server 2003 部署工具包的作业帮助](https://microsoft.com/download/details.aspx?id=9608)，下载 Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip，并打开 "站点和关联的站点链接" ( # A1) 。

## <a name="in-this-guide"></a>本指南包含的内容

[设置站点链接属性](Setting-Site-Link-Properties.md)
