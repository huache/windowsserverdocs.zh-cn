---
ms.assetid: 638c89bd-87e6-484b-9d2e-8ae2a74227e5
title: 设置服务通信证书
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 6549b120768bf01c43f38fc5252529e971043eaa
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956049"
---
# <a name="set-a-service-communications-certificate"></a>设置服务通信证书


Active Directory 联合身份验证服务中的联合服务器 \( AD FS \) 使用服务通信证书来保护 \( \) 与 web 客户端或联合服务器代理的安全套接字层 SSL 通信的 Web 服务通信。

> [!NOTE]  
> 服务通信证书与 SSL 证书不同。 若要更改 AD FS SSL 证书，你将需要使用 Powershell。 按照[本文](../operations/manage-ssl-certificates-ad-fs-wap.md)中的指导进行操作。


你可以使用以下过程，通过中的 AD FS 管理 "管理单元来更改服务通信证书 \- 。  

> [!NOTE]  
> "AD FS 管理" 管理单元 \- 是指作为服务通信证书的联合服务器的服务器身份验证证书。  

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477) \( http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 83477 \) 。   

### <a name="to-set-a-service-communications-certificate"></a>设置服务通信证书  

1.  在 "**开始**" 屏幕上，键入 "**AD FS 管理**"，然后按 enter。  

2.  在控制台树中，双击 \- "**服务**"，然后单击 "**证书**"。  

3.  在 "**操作**" 窗格中，单击 "**设置服务通信证书**" 链接。  

4.  在 "**选择服务通信证书**" 对话框中，导航到要设置为服务通信证书的证书文件，选择证书文件，然后单击 "**打开**"。  

## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  

[联合服务器的证书要求](../design/certificate-requirements-for-federation-servers.md)  
