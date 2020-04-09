---
ms.assetid: e1f2ce2d-b24f-4ccd-8add-9e69419fc6c1
title: 将服务器身份验证证书导入到默认网站
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 3f02358167b024247f934a46218028575e393ba9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855400"
---
# <a name="import-a-server-authentication-certificate-to-the-default-web-site"></a>将服务器身份验证证书导入到默认网站

从证书颁发机构获取服务器身份验证证书之后 \(CA\)，必须在服务器场中每个联合服务器或联合服务器代理的默认网站上手动安装该证书。  
  
对于 Web 服务器，必须在相应的网站或你的联合应用程序所在的虚拟目录上手动安装服务器身份验证证书。  
  
如果你要设置某个服务器场，请务必在服务器场中的每个服务器上执行同样的过程（使用完全相同的设置）。  
  
> [!NOTE]  
> 中的 AD FS 管理 "管理单元\-是指作为服务通信证书的联合服务器的服务器身份验证证书。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
### <a name="to-import-a-server-authentication-certificate-to-the-default-web-site"></a>将服务器身份验证证书导入到默认网站  
  
1.  在 "**开始**" 屏幕上，键入 "**Internet Information Services \(IIS\) 管理器**"，然后按 enter。  
  
2.  在控制台树中单击 **“ComputerName”** 。  
  
3.  在中心窗格中，双击 "**服务器证书**"\-"。  
  
4.  在 **“操作”** 窗格中单击 **“导入”** 。  
  
5.  在 "**导入证书**" 对话框中，单击 " **...** " 按钮。  
  
6.  浏览到 pfx 证书文件所在的位置，突出显示它，然后单击 **“打开”** 。  
  
7.  键入该证书的密码，然后单击 **“确定”** 。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  
[联合服务器的证书要求](https://technet.microsoft.com/library/dd807040.aspx)  
  
[联合服务器代理的证书要求](https://technet.microsoft.com/library/dd807054.aspx)  
   
  

