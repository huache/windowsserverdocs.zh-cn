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
ms.openlocfilehash: 47d619803133a29bd0217b738577c93522f1ab59
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815020"
---
# <a name="add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>为联合服务器将主机 (A) 资源记录添加到企业 DNS



要使企业网络上的客户端成功地使用 Windows 集成身份验证访问联合服务器，必须先在公司域名系统中创建一个 \(\) 资源记录的主机 \(DNS\)，该 DNS 解析帐户联合服务器的主机名称 \(例如，fs.fabrikam.com\) 到联合服务器或联合服务器群集的 IP 地址。 你可以使用以下过程向联合服务器的企业 DNS 添加主机 \(\) 资源记录。  
  
**Administrators**中的成员身份或同等身份是完成此过程所需的最低要求。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
### <a name="to-add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>向联合服务器的企业 DNS 添加主机 \(\) 资源记录  
  
1.  在企业网络的 DNS 服务器上，打开中的 DNS snap\-。  
  
2.  在控制台树中，\-右键单击适用的正向查找区域，然后单击 "**新建主机 \(A 或 AAAA\)** "。  
  
3.  在 "**名称**" 中，仅键入联合服务器或联合服务器群集的计算机名称;例如，对于完全限定的域名 \(FQDN\) fs.fabrikam.com，请键入**fs**。  
  
4.  在 " **ip 地址**" 中，键入联合服务器或联合服务器群集的 IP 地址，例如192.168.1.4。  
  
5.  单击 **“添加主机”** 。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[联合服务器的名称解析要求](https://technet.microsoft.com/library/dd807055.aspx)  
  

