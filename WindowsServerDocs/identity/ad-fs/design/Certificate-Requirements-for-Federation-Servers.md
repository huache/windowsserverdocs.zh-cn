---
ms.assetid: 9831b421-8fb7-4e15-ac27-c013cbca6d05
title: 联合服务器的证书要求
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: fcf78fa6242c10d469320ce3803da94134576c8b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954363"
---
# <a name="certificate-requirements-for-federation-servers"></a>联合服务器的证书要求

在任何 Active Directory 联合身份验证服务 \( AD FS \) 设计中，都必须使用各种证书来保护通信，并促进 Internet 客户端与联合服务器之间的用户身份验证。 每个联合服务器必须具有服务通信证书和令牌 \- 签名证书，然后才能参与 AD FS 通信。 下表描述了与联合服务器关联的证书类型。

|证书类型|描述|
|--------------------|---------------|
|令牌 \- 签名证书|令牌 \- 签名证书是一个 X509 证书。 联合服务器使用关联 \/ 的公钥私钥对，对它们产生的所有安全令牌进行数字签名。 这包括已发布的联合元数据和项目分辨率请求的签名。<p>可以在 \- AD FS 管理 "管理单元中配置多个令牌签名证书 \- ，以允许在一个证书即将过期时使用证书滚动更新。 默认情况下，列表中的所有证书都已发布，但 AD FS 仅使用主要令牌 \- 签名证书来对令牌进行实际签名。 你选择的所有证书都必须具有相应的私钥。<p>有关详细信息，请参阅[令牌签名证书](Token-Signing-Certificates.md)和[添加令牌签名证书](../../ad-fs/deployment/Add-a-Token-Signing-Certificate.md)。|
|服务通信证书|联合服务器使用服务器身份验证证书，即 Windows Communication Foundation \( WCF 消息安全的服务通信 \) 。 默认情况下，此证书与联合服务器用作 \( Internet Information Services IIS 中安全套接字层 SSL 证书的证书相同 \) \( \) 。 **注意：**"AD FS 管理" 管理单元 \- 是指作为服务通信证书的联合服务器的服务器身份验证证书。<p>有关详细信息，请参阅[服务通信证书](Service-Communications-Certificates.md)和[设置服务通信证书](../../ad-fs/deployment/Set-a-Service-Communications-Certificate.md)。<p>由于服务通信证书必须受客户端计算机信任，因此我们建议你使用由受信任的证书颁发机构 CA 签名的证书 \( \) 。 你选择的所有证书都必须具有相应的私钥。|
|安全套接字层 \( SSL \) 证书|联合服务器使用 SSL 证书来保护与 Web 客户端以及与联合服务器代理的 SSL 通信的 Web 服务通信。<p>由于 SSL 证书必须受客户端计算机信任，因此我们建议你使用由受信任的 CA 签名的证书。 你选择的所有证书都必须具有相应的私钥。|
|令牌 \- 解密证书|此证书用于解密此联合服务器收到的令牌。<p>你可以有多个解密证书。 这样，资源联合服务器就可以在将新证书设置为主解密证书后，能够解密使用较旧的证书颁发的令牌。 所有证书都可以用于解密，但是 \- 在联合元数据中只实际发布主令牌解密证书。 你选择的所有证书都必须具有相应的私钥。<p>有关详细信息，请参阅[添加令牌解密证书](../../ad-fs/deployment/Add-a-Token-Decrypting-Certificate.md)。|

您可以通过用于 IIS 的 Microsoft 管理控制台 \( mmc 管理单元请求服务通信证书，请求并安装 SSL 证书或服务通信证书 \) \- 。 有关使用 SSL 证书的更多常规信息，请参阅 iis [7.0：在 iis 7.0 中配置安全套接字层](https://go.microsoft.com/fwlink/?LinkID=108544)和[iis 7.0：在 Iis 中配置服务器证书 7.0](https://go.microsoft.com/fwlink/?LinkID=108545) 。

> [!NOTE]
> 在 AD FS 可以将用于数字签名的安全哈希算法 \( SHA \) 级别更改为 sha \- 1 或 sha \- 256 \( 更安全 \) 。 AD FSdoes 不支持通过其他哈希方法使用证书，如 MD5，这 \( 是与 Makecert.exe 命令行工具一起使用的默认哈希算法 \- \) 。 作为安全性最佳做法，我们建议使用 \- \( 默认情况下为所有签名设置的 SHA 256 \) 。 \-仅在必须与不支持使用 sha 256 通信的产品（ \- 如非 \- Microsoft 产品或 AD FS 1）互操作的情况下，才建议使用 SHA 1。 *x*。

## <a name="determining-your-ca-strategy"></a>确定 CA 策略
AD FS 不需要由 CA 颁发证书。 不过，SSL 证书 \( 默认情况下也用作服务通信证书的证书 \) 必须由 AD FS 的客户端信任。 建议你不要 \- 为这些证书类型使用自签名证书。

> [!IMPORTANT]
> 使用自 \- 签名，在生产环境中的 SSL 证书可以使帐户伙伴组织中的恶意用户能够控制资源伙伴组织中的联合服务器。 存在此安全风险的原因 \- 是自签名证书是根证书。 它们必须添加到另一个联合服务器的受信任的根存储中， \( 例如资源联合服务器 \) ，这可能会使该服务器容易受到攻击。

从 CA 收到证书后，请确保将所有的证书导入到本地计算机的个人证书存储中。 可以通过证书 MMC 管理单元将证书导入到个人存储 \- 中。

作为使用中的 "证书" 管理器的替代方法 \- ，你还可以在 \- 将 ssl 证书分配给默认网站时，使用 IIS 管理器管理单元导入 ssl 证书。 有关详细信息，请参阅将[服务器身份验证证书导入到默认](../../ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)网站。

> [!NOTE]
> 在将成为联合服务器的计算机上安装 AD FS 软件之前，请确保这两个证书位于本地计算机的 "个人" 证书存储中，并且已将 SSL 证书分配给默认网站。 有关设置联合服务器所需的任务顺序的详细信息，请参阅[清单：设置联合服务器](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md)。

根据你的安全和预算需求，请仔细考虑哪些证书将由公共 CA 或企业 CA 来获得。 下图显示了关于给定证书类型的建议的 CA 颁发者。 此建议反映了 \- 有关安全和成本的最佳实践方法。

![证书要求](media/adfs2_fedserver_certstory_1.png)

## <a name="certificate-revocation-lists"></a>证书吊销列表
如果你使用的任何证书具有 CRL，则具有配置证书的服务器必须能够联系分发 CRL 的服务器。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
