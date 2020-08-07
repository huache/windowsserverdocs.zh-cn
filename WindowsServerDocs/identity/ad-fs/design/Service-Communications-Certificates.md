---
ms.assetid: 95e82190-68c5-4e40-87b1-f1bd816ef4e9
title: 服务通信证书
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 377b6f9053a5805f6a13f6a865185da6965f9966
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972074"
---
# <a name="service-communications-certificates"></a>服务通信证书

对于使用 WCF 消息安全的方案，联合服务器需要使用服务通信证书。

## <a name="service-communication-certificate-requirements"></a>服务通信证书要求
服务通信证书必须满足以下要求才能处理 AD FS：

-   服务通信证书必须包含服务器身份验证增强型密钥用法 \( EKU \) 扩展。

-   证书吊销列表 \( \) 必须可从服务通信证书到根 CA 证书的证书链中的所有证书访问 crl。 根 CA 还必须受信任此联合服务器的任何联合服务器代理和 Web 服务器信任。

-   服务通信证书中使用的使用者名称必须与联合身份验证服务的属性中的联合身份验证服务名称匹配。

## <a name="deployment-considerations-for-service-communication-certificates"></a>服务通信证书的部署注意事项
配置服务通信证书，以便所有联合服务器使用同一证书。 如果要部署联合 Web 单一 \- 登录 \- \( SSO \) 设计，建议由公共 CA 颁发服务通信证书。 可以通过中的 IIS 管理器管理单元来请求和安装这些证书 \- 。

在 \- 测试实验室环境中，可以在联合服务器上成功使用自签名的服务通信证书。 但是，对于生产环境，建议从公共 CA 获取服务通信证书。 以下原因说明不应使用自 \- 签名的服务通信证书进行实时部署：

-   自 \- 签名的 SSL 证书必须添加到资源伙伴组织中每台联合服务器上的受信任根存储中。 虽然这种情况并不允许攻击者损害资源联合服务器，但信任自 \- 签名证书确实会增加计算机的攻击面，如果证书签名者不可信，则可能会导致安全漏洞。

-   它会导致用户体验不佳。 当客户端尝试访问显示以下消息的联合资源时，客户端将收到安全警报提示： "此安全证书是由你未选择信任的公司颁发的。" 这是预期的行为，因为自 \- 签名证书不受信任。

    > [!NOTE]
    > 如有必要，你可以通过使用组策略将自 \- 签名证书手动推送到将尝试访问 AD FS 站点的每台客户端计算机上的受信任根存储中来解决此问题。

-   Ca 提供了其他 \- 基于证书的功能，如私钥存档、续订和吊销，这些功能不是由自 \- 签名证书提供的。


