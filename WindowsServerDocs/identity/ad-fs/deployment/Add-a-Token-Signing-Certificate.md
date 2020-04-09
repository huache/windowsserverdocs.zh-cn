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
ms.openlocfilehash: 9b737cf8c9efb89ef9b3befaa1875b273bfcadf9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80814930"
---
# <a name="add-a-token-signing-certificate"></a>添加令牌签名证书


Active Directory 联合身份验证服务 \(AD FS\) 中的联合服务器需要令牌\-签名证书，以防止攻击者篡改或伪造安全令牌，以尝试获取对联合资源的未经授权的访问。 每个令牌\-签名证书都包含加密私钥和公钥，用于通过私钥\) 安全令牌对 \(进行数字签名。 稍后，伙伴联合服务器收到这些密钥后，它们将通过加密安全令牌的公钥\) 来验证 \(真实性。  
  
> [!CAUTION]  
> 用于令牌\-签名的证书对联合身份验证服务稳定性至关重要。 由于为此目的配置的任何证书丢失或未计划删除都可能中断服务，因此应备份任何为此目的配置的证书。  
  
令牌\-签名证书应链接到联合身份验证服务中的受信任的根。 你可以使用以下过程将令牌\-签名证书添加到中的 "AD FS 管理" 管理单元\-，从已导出的文件。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)\(http：\/\/go.microsoft.com\/fwlink\/？LinkId\=83477\)。   
  
### <a name="to-add-a-token-signing-certificate"></a>\-签名证书添加令牌  
  
1.  在 "**开始**" 屏幕上，键入 "**AD FS 管理**"，然后按 enter。  
  
2.  在控制台树中，\-双击 "**服务**"，然后单击 "**证书**"。  
  
3.  在 "**操作**" 窗格中，单击 "**添加令牌\-签名证书**" 链接。  
  
4.  在 "**浏览证书文件**" 对话框中，导航到要添加的证书文件，选择证书文件，然后单击 "**打开**"。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[联合服务器的证书要求](https://technet.microsoft.com/library/dd807040.aspx)  
  

