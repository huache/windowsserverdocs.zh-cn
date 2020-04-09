---
ms.assetid: c50ecc6a-9504-4b4a-816f-e762dcf3a95e
title: 安装联合身份验证服务代理角色服务
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 8d2ff177c821baf31bb5453b7c50e3eadca2aab7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855380"
---
# <a name="install-the-federation-service-proxy-role-service"></a>安装联合身份验证服务代理角色服务

使用先决条件应用程序和证书配置计算机后，便可以安装 Active Directory 联合身份验证服务 \(AD FS\)的联合身份验证服务代理角色服务。 你可以使用以下过程安装联合身份验证服务代理角色服务。 在计算机上安装联合身份验证服务代理角色服务时，该计算机将成为联合服务器代理。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
### <a name="to-install-the-federation-service-proxy-role-service-using-the-server-manager"></a>使用服务器管理器安装联合身份验证服务代理角色服务
  
1.  在 "**开始**" 屏幕上，键入**服务器管理器**，然后按 enter。  
  
2.  单击 **“管理”** ，然后单击 **“添加角色和功能”** 以启动添加角色和功能向导。  
  
3.  在 **“开始之前”** 页上，单击 **“下一步”** 。  
  
4.  在 "**选择安装类型**" 页上，单击 "**基于角色\-或基于功能\-安装**"，然后单击 "**下一步**"。  
  
5.  在 **“选择目标服务器”** 页上，单击 **“从服务器池中选择服务器”** ，确认目标计算机已突出显示，然后单击 **“下一步”** 。  
  
6.  在 "**选择服务器角色**" 页上，单击 "**远程访问**"，然后单击 "下一步"。  
  
    > [!NOTE]  
    > 如果系统提示你安装其他 .NET Framework 或 Windows 进程激活服务功能，请单击 **“添加功能”** 以安装这些功能。  
  
7. 在 **“选择角色服务”** 页上，选中 **“联合身份验证服务代理”** 复选框，然后单击 **“下一步”** 。  

8. 确认 **“确认安装选择”** 页上的信息后，选中 **“如果需要，自动重新启动目标服务器”** 复选框，然后单击 **“安装”** 。  
  
13. 在 **“安装进度”** 页上，确认已正确安装所有项目，然后单击 **“关闭”** 。  

### <a name="to-install-the-federation-service-proxy-role-service-using-powershell"></a>使用 PowerShell 安装联合身份验证服务代理角色服务

1. 打开 Windows PowerShell （以管理员身份运行）

2. 键入以下命令并按**enter**：

        Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools



  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  

