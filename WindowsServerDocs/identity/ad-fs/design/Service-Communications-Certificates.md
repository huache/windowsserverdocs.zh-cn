---
ms.assetid: 95e82190-68c5-4e40-87b1-f1bd816ef4e9
title: 服务通信证书
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 91ef716f518676fe9cf42b2136afcbcd42c50946
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858520"
---
# <a name="service-communications-certificates"></a>服务通信证书

对于使用 WCF 消息安全的方案，联合服务器需要使用服务通信证书。  
  
## <a name="service-communication-certificate-requirements"></a>服务通信证书要求  
服务通信证书必须满足以下要求才能处理 AD FS：  
  
-   服务通信证书必须包括服务器身份验证增强型密钥用法 \(EKU\) 扩展。  
  
-   证书吊销列表 \(Crl\) 必须可从服务通信证书到根 CA 证书的证书链中的所有证书访问。 根 CA 还必须受信任此联合服务器的任何联合服务器代理和 Web 服务器信任。  
  
-   服务通信证书中使用的使用者名称必须与联合身份验证服务的属性中的联合身份验证服务名称匹配。  
  
## <a name="deployment-considerations-for-service-communication-certificates"></a>服务通信证书的部署注意事项  
配置服务通信证书，以便所有联合服务器使用同一证书。 如果要部署 \(SSO\) 设计上的联合 Web 单一\-登录\-，建议由公共 CA 颁发服务通信证书。 可以通过中的 IIS 管理器 snap\-来请求和安装这些证书。  
  
在测试实验室环境中，可以在联合服务器上成功使用自\-签名的服务通信证书。 但是，对于生产环境，建议从公共 CA 获取服务通信证书。 下面是不应使用自\-签名的服务通信证书进行实时部署的原因：  
  
-   必须向资源伙伴组织中的每台联合服务器上的受信任的根存储区中添加一个自行\-签名的 SSL 证书。 虽然这种方法本身不能使攻击者损害资源联合服务器，但信任自我\-签名证书确实会增加计算机的攻击面，如果证书签名者不可信，则可能会导致安全漏洞。  
  
-   它会导致用户体验不佳。 当客户端尝试访问显示以下消息的联合资源时，客户端将收到安全警报提示： "此安全证书是由你未选择信任的公司颁发的。" 这是预期的行为，因为自\-签名证书不受信任。  
  
    > [!NOTE]  
    > 如有必要，你可以通过使用组策略在将尝试访问 AD FS 站点的每台客户端计算机上的受信任的根存储区中手动向下推送自\-签名证书，从而解决此问题。  
  
-   Ca 提供附加的基于证书\-功能，如私钥存档、续订和吊销，这些功能不是由自\-签名证书提供的。  
  

