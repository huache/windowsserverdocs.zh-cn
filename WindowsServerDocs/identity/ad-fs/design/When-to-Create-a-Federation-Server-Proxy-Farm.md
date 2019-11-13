---
ms.assetid: ad0bf21d-2ace-4565-b1f5-ce57c8eb2689
title: 何时创建联合服务器代理场
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 247daf1b9b49124188f6bb16bce7da381fe997ef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402430"
---
# <a name="when-to-create-a-federation-server-proxy-farm"></a>何时创建联合服务器代理场

Active Directory 联合身份验证服务如果 \(AD FS\) 部署，并且想要为代理部署提供容错、负载\-平衡和可伸缩性时，请考虑安装其他联合服务器代理。 在同一外围网络中创建两个或多个联合服务器代理，并配置每个代理以保护相同的 AD FS 联合身份验证服务创建联合服务器代理场。  
  
您可以使用 AD FS 联合服务器代理配置向导创建联合服务器代理场或将其他联合服务器代理安装到现有场。 有关详细信息，请参阅 [When to Create a Federation Server Proxy](When-to-Create-a-Federation-Server-Proxy.md)。  
  
必须先在一个 IP 地址和一个域名系统 \(DNS\) 完全限定的域名 \(FQDN\)，然后才能将所有联合服务器代理作为场一起工作。 可以通过在外围网络内部署 \(NLB\) 来对服务器进行群集。 下表中的任务需要适当地配置 NLB，以便群集到场中的联合服务器代理。  
  
有关如何使用 Microsoft NLB 技术为群集配置 FQDN 的详细信息，请参阅[指定群集参数](https://go.microsoft.com/fwlink/?linkid=74651)。  
  
## <a name="configuring-federation-server-proxies-for-a-farm"></a>为场配置联合服务器代理  
下表描述了必须完成的任务，以便每个联合服务器代理都可以参与到场。  
  
|任务|描述|  
|--------|---------------|  
|将场中的所有代理指向相同的 AD FS 联合身份验证服务名称|创建联合服务器代理时，必须为将参与场的所有联合服务器代理在 AD FS 联合服务器代理配置向导中键入相同的联合身份验证服务名称。 联合服务器代理使用构成此 DNS 主机名的 URL 来确定它与哪个 AD FS 联合身份验证服务实例联系在一起。<br /><br />有关详细信息，请参阅 [Configure a Computer for the Federation Server Proxy Role](../../ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md)。|  
|获取和共享证书|你可以从公共证书颁发机构 \(CA\)（例如 VeriSign）获取服务器身份验证证书，然后配置该证书，以便所有联合服务器代理在每个联合服务器代理的默认网站上共享相同证书的相同私钥部分。 若要共享证书，必须在每个联合服务器代理的默认网站上安装相同的服务器身份验证证书。 有关详细信息，请参阅将[服务器身份验证证书导入到默认](../../ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)网站。<br /><br />有关详细信息，请参阅 [Certificate Requirements for Federation Server Proxies](Certificate-Requirements-for-Federation-Server-Proxies.md)。|  
  
有关添加新的联合服务器代理以创建联合服务器代理场的详细信息，请参阅[清单：设置联合服务器代理](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
