---
ms.assetid: 026747c7-4c34-41c7-b7ea-27f9a7f64a35
title: 为联合服务器将主机 (A) 资源记录添加到企业 DNS
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: fdf75408e4627fb587f95e9b1c8d2fb93c8e9410
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86960039"
---
# <a name="add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>为联合服务器将主机 (A) 资源记录添加到企业 DNS



为了使企业网络上的客户端能够使用 Windows 集成身份验证成功访问联合服务器， \( \) 必须先在公司域名系统 DNS 中创建一个主机 a 资源记录， \( 该 DNS 将 \) 解析帐户联合服务器的主机名 \( ，例如，fs.fabrikam.com \) 为联合服务器或联合服务器群集的 IP 地址。 你可以使用以下过程为联合服务器将主机 \( a \) 资源记录添加到公司 DNS 中。  
  
**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。   
  
### <a name="to-add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>向 \( \) 联合服务器的企业 DNS 添加主机 a 资源记录  
  
1.  在企业网络的 DNS 服务器上，打开 DNS 管理单元 \- 。  
  
2.  在控制台树中，右键 \- 单击适用的正向查找区域，然后单击 "**新建主机 \( A 或 \) AAAA**"。  
  
3.  在 "**名称**" 中，仅键入联合服务器或联合服务器群集的计算机名称;例如，对于完全限定的域名 \( FQDN \) fs.fabrikam.com，键入**fs**。  
  
4.  在 " **ip 地址**" 中，键入联合服务器或联合服务器群集的 IP 地址，例如192.168.1.4。  
  
5.  单击 **“添加主机”**。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[联合服务器的名称解析要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055(v=ws.11))  
  
