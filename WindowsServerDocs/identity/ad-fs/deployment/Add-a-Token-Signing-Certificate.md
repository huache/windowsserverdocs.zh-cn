---
ms.assetid: bbb84ea6-7e31-4442-85ab-a9447e7c19e8
title: 添加令牌签名证书
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: b2fc8d0d99530bf3700cac98e483d45f000af4a5
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966639"
---
# <a name="add-a-token-signing-certificate"></a>添加令牌签名证书


Active Directory 联合身份验证服务 AD FS 中的联合服务器 \( \) 需要令牌 \- 签名证书，以防止攻击者篡改或伪造安全令牌，以尝试获取对联合资源的未经授权的访问。 每个令牌 \- 签名证书都包含加密私钥和公钥，这些密钥用于 \( 通过私钥以安全令牌进行数字签名 \) 。 稍后，伙伴联合服务器收到这些密钥后，它们将 \( 通过加密安全令牌的公钥来验证真实性 \) 。  
  
> [!CAUTION]  
> 用于令牌签名的证书对于 \- 联合身份验证服务的稳定性至关重要。 由于为此目的配置的任何证书丢失或未计划删除都可能中断服务，因此应备份任何为此目的配置的证书。  
  
令牌 \- 签名证书应链接到联合身份验证服务中的受信任的根。 你可以使用以下过程将令牌 \- 签名证书添加到中的 "AD FS 管理" 管理单元 \- 中，从你导出的文件。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477) \( http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 83477 \) 。   
  
### <a name="to-add-a-token-signing-certificate"></a>添加令牌 \- 签名证书  
  
1.  在 "**开始**" 屏幕上，键入 "**AD FS 管理**"，然后按 enter。  
  
2.  在控制台树中，双击 \- "**服务**"，然后单击 "**证书**"。  
  
3.  在 "**操作**" 窗格中，单击 "**添加令牌 \- 签名证书**" 链接。  
  
4.  在 "**浏览证书文件**" 对话框中，导航到要添加的证书文件，选择证书文件，然后单击 "**打开**"。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[联合服务器的证书要求](../design/certificate-requirements-for-federation-servers.md)  
  
