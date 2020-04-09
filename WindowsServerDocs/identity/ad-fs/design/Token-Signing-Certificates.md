---
ms.assetid: 98c5ef45-2bcb-4f87-86c8-5ac6c16a6097
title: 令牌签名证书
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 24b095827ad074dbe249a9d4decd8edeecbb3603
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858780"
---
# <a name="token-signing-certificates"></a>令牌签名证书

联合服务器需要令牌\-签名证书，以防止攻击者在尝试获取对联合资源的未授权访问权限时更改或伪造安全令牌。 与令牌\-签名证书结合使用的私有\/公钥对是任何联合合作关系的最重要验证机制，因为这些密钥验证安全令牌是否由有效的伙伴联合服务器颁发，并且在传输过程中未修改该令牌。  
  
## <a name="token-signing-certificate-requirements"></a>令牌\-签名证书要求  
令牌\-签名证书必须满足以下要求才能使用 AD FS：  
  
-   若要\-签名证书以成功对安全令牌进行签名，令牌\-签名证书必须包含私钥。  
  
-   AD FS 服务帐户必须在本地计算机的个人存储中具有对令牌\-签名证书私钥的访问权限。 这由安装程序执行。 你还可以使用中的 AD FS 管理 "管理单元\-来确保此访问权限，前提是你随后将令牌\-签名证书。  
  
> [!NOTE]  
> 这是一种公钥基础结构 \(PKI\) 最佳做法，不会出于多种目的共享私钥。 因此，请不要使用在联合服务器上安装的服务通信证书作为令牌\-签名证书。  
  
## <a name="how-token-signing-certificates-are-used-across-partners"></a>如何跨伙伴使用令牌\-签名证书  
每个令牌\-签名证书都包含加密私钥和公钥，用于通过私钥\) 安全令牌对 \(进行数字签名。 稍后，伙伴联合服务器收到这些密钥后，这些密钥将通过加密安全令牌的公钥\) 来验证 \(真实性。  
  
因为每个安全令牌由帐户伙伴进行数字签名，资源伙伴可以验证安全令牌是否确实由帐户伙伴颁发且未进行修改。 数字签名由合作伙伴令牌\-签名证书的公钥部分进行验证。 验证签名后，资源联合服务器将为其组织生成其自己的安全令牌，并将具有自己的令牌的安全令牌签名\-签名证书。  
  
对于联合身份验证伙伴环境，当 CA 颁发\-签名证书的令牌时，请确保：  
  
1.  证书吊销列表 \(Crl\) 证书可用于信任联合服务器的信赖方和 Web 服务器。  
  
2.  根 CA 证书受信任的信赖方和 Web 服务器信任。  
  
资源伙伴中的 Web 服务器使用令牌的公钥\-签名证书来验证是否已由资源联合服务器对安全令牌进行签名。 然后，Web 服务器允许对客户端进行适当的访问。  
  
## <a name="deployment-considerations-for-token-signing-certificates"></a>令牌\-签名证书的部署注意事项  
在新的 AD FS 安装中部署第一台联合服务器时，必须获取令牌\-签名证书，并将其安装在该联合服务器上的本地计算机个人证书存储中。 可以通过从企业 CA 或公共 CA 请求证书，或通过创建自\-签名证书，来\-签名证书。  
  
部署 AD FS 场时，令牌\-签名证书的安装方式会有所不同，具体取决于你创建服务器场的方式。  
  
获取用于部署的令牌\-签名证书时，可以考虑两个服务器场选项：  
  
-   在场中的所有联合服务器之间共享一个令牌\-签名证书的私钥。  
  
    在联合服务器场环境中，建议所有联合服务器共享 \(或重复使用\) 同一令牌\-签名证书。 只要颁发的证书标记为可导出，你就可以在联合服务器上的 CA 中安装单个令牌\-签名证书，然后导出私钥。  
  
    如下图所示，\-签名证书的单个令牌的私钥可以共享到场中的所有联合服务器。 如果你计划从公共 CA 获取令牌\-签名证书，则此选项（与以下 "唯一标记\-签名证书" 选项相比）可降低成本。  
  
![令牌签名](media/adfs2_fedserver_certstory_3.gif)  
  
-   在场中的每个联合服务器\-签名证书都有唯一的令牌。  
  
    在整个场中使用多个唯一的证书时，该服务器场中的每个服务器都会使用其自己的唯一私钥对令牌进行签名。  
  
    如下图所示，可以为场中的每个联合服务器\-签名证书单独获取令牌。 如果你计划从公共 CA 获取令牌\-签名证书，则此选项开销更高。  
  
![令牌签名](media/adfs2_fedserver_certstory_4.gif)  
  
有关将 Microsoft 证书服务用作企业 CA 时安装证书的信息，请参阅[iis 7.0：在 iis 7.0 中创建域服务器证书](https://go.microsoft.com/fwlink/?LinkId=108548)。  
  
有关从公共 CA 安装证书的信息，请参阅[IIS 7.0：请求 Internet 服务器证书](https://go.microsoft.com/fwlink/?LinkId=108549)。  
  
有关安装自\-签名证书的信息，请参阅 iis [7.0：在 iis 7.0 中创建自\-签名服务器证书](https://go.microsoft.com/fwlink/?LinkID=108271)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
