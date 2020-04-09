---
ms.assetid: e33673ff-ea1c-4476-a549-3bf5899a47dd
title: 安装联合身份验证服务角色服务
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 4952fad89502f9d81faab86cfd2e0e056543defd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855370"
---
# <a name="install-the-federation-service-role-service"></a>安装联合身份验证服务角色服务

现在，你已使用先决条件应用程序和证书正确配置了计算机，接下来可以安装 Active Directory 联合身份验证服务 \(AD FS\)的联合身份验证服务角色服务。 在计算机上安装联合身份验证服务时，该计算机将成为联合服务器。  
  
> [!NOTE]  
> 对于 \(SSO\) 设计上的联合 Web 单一\-Sign\-，在帐户伙伴组织和资源伙伴组织中必须至少有一个联合服务器。 有关详细信息，请参阅[放置联合服务器的位置](https://technet.microsoft.com/library/dd807127.aspx)。  
  
你可以使用以下过程在将成为第一台联合服务器的计算机上或在将成为现有联合服务器场的联合服务器的计算机上安装 AD FS 的联合身份验证服务角色服务。  
  
## <a name="prerequisites"></a>先决条件  
开始此过程之前，请验证是否已安装了具有私钥的 SSL 证书，或已将其导入到本地证书存储 \(个人存储\)。 如果你将使用证书颁发机构 \(CA\)颁发的令牌\-签名证书，则在开始此过程之前，请确保已安装了具有私钥的令牌\-签名证书，或将其导入到本地证书存储 \(个人存储\)。 作为替代方法，你可以使用添加角色向导创建自\-签名证书的签名证书\-，如本过程中所述。 有关令牌\-签名证书的详细信息，请参阅[联合服务器的证书要求](https://technet.microsoft.com/library/dd807040.aspx)。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)\(http：\/\/go.microsoft.com\/fwlink\/？LinkId\=83477\)。   
  
#### <a name="to-install-the-federation-service-role-service"></a>安装联合身份验证服务角色服务  
  
1.  在 "**开始**" 屏幕上，键入**服务器管理器**，然后按 enter。  
  
2.  单击 **“管理”** ，然后单击 **“添加角色和功能”** 以启动添加角色和功能向导。  
  
3.  在 **“开始之前”** 页上，单击 **“下一步”** 。  
  
4.  在 "**选择安装类型**" 页上，单击 "**基于角色\-或基于功能\-安装**"，然后单击 "**下一步**"。  
  
5.  在 **“选择目标服务器”** 页上，单击 **“从服务器池中选择服务器”** ，确认目标计算机已突出显示，然后单击 **“下一步”** 。  
  
6.  在 **“选择服务器角色”** 页上，单击 **“Active Directory 联合身份验证服务”** ，然后单击“下一步”。  
  
    > [!NOTE]  
    > 如果系统提示你安装其他 .NET Framework 或 Windows 进程激活服务功能，请单击 **“添加功能”** 以安装这些功能。  
  
7.  在 **“选择功能”** 页上，确认已设置这些功能，然后单击 **“下一步”** 。  
  
8.  在 " **Active Directory 联合身份验证服务 \(AD FS\)** " 页上，单击 "**下一步**"。  
  
9. 在 **“选择角色服务”** 页上，选中 **“联合身份验证服务”** 复选框，然后单击 **“下一步”** 。  
  
10. 在 " **Web 服务器角色 \(IIS\)** " 页上，单击 "**下一步**"。  
  
11. 在 **“选择角色服务”** 页上，单击 **“下一步”** 。  
  
12. 确认 **“确认安装选择”** 页上的信息后，选中 **“如果需要，自动重新启动目标服务器”** 复选框，然后单击 **“安装”** 。  
  
13. 在 **“安装进度”** 页上，确认已正确安装所有项目，然后单击 **“关闭”** 。  
  

