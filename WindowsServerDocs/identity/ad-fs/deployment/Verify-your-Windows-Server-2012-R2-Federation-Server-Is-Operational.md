---
ms.assetid: 1115d276-00f6-4c23-9278-eedcc31295d8
title: 验证 Windows Server 2012 R2 联合服务器是否正常运行
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 98de8166756b5741c215831aa3a5ca47d4c0d54b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855830"
---
# <a name="verify-your-windows-server-2012-r2-federation-server-is-operational"></a>验证 Windows Server 2012 R2 联合服务器是否正常运行



你可以使用以下过程验证联合服务器正常工作；也即，同一网络中的任何客户端都可以到达新的联合服务器。  
  
若要完成此过程，至少需要是本地计算机上的**用户**组、**备份操作员**组、**高级用户**组、**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
### <a name="procedure-1-to-verify-that-a-federation-server-is-operational"></a>步骤1：验证联合服务器是否正常运行  
  
1.  若要验证是否在联合服务器上正确配置了 Internet Information Services \(的 IIS\)，请登录到与联合服务器位于同一个林中的客户端计算机。  
  
2.  打开浏览器窗口，在地址栏中键入联合服务器的 DNS 主机名，然后为新联合服务器将 \/adfs\/fs\/federationserverservice 添加到该窗口中，例如：  
  
    **https：\/\/fs1.fabrikam.com\/adfs\/fs\/federationserverservice**  
  
3.  按 Enter，然后在联合服务器计算机上完成下一过程。 如果看到消息 "**此网站的安全证书有问题**"，请单击 "**继续访问此网站**"。  
  
    预期输出为显示 XML 以及服务说明文档。 如果显示此页，则联合服务器上的 IIS 正常工作且成功提供页面。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
### <a name="procedure-2-to-verify-that-a-federation-server-is-operational"></a>步骤2：验证联合服务器是否正常运行  
  
1.  以管理员身份登录到新的联合服务器。  
  
2.  在 "**开始**" 屏幕上，键入**事件查看器**，然后按 enter。  
  
3.  在详细信息窗格中，\-双击 "**应用程序和服务日志**"，\-双击 " **AD FS 事件**"，然后单击 "**管理员**"。  
  
4.  在 "**事件 id** " 列中，查找事件 id 100。 如果正确配置了联合服务器，则会在事件查看器的应用程序日志中看到一个新事件，事件 ID 为100。 此事件验证联合服务器是否能够成功地与联合身份验证服务通信。  
  
## <a name="see-also"></a>另请参阅 

[AD FS 部署](../../ad-fs/AD-FS-Deployment.md)  

[Windows Server 2012 R2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[部署联合服务器场](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
   
  

