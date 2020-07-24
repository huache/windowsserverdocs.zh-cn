---
ms.assetid: 5a1ae56b-adcb-447e-9e34-c0629d7cb241
title: 手动配置联合服务器场的服务帐户
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 5d0495d43eecd2508a6535411ef4e226db0ebacf
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86964789"
---
# <a name="manually-configure-a-service-account-for-a-federation-server-farm"></a>手动配置联合服务器场的服务帐户

如果要在 Active Directory 联合身份验证服务 AD FS 中配置联合服务器场环境 \( \) ，则必须在 \( \) 服务器场将驻留 Active Directory 域服务 AD DS 中创建和配置专用服务帐户。 然后配置服务器场中的每个联合服务器以使用此帐户。 如果希望允许企业网络上的客户端计算机使用 Windows 集成身份验证向 AD FS 场中的任何联合服务器进行身份验证，则必须在组织中完成以下任务。  

> [!IMPORTANT]
> 到 AD FS 3.0 （Windows Server 2012 R2），AD FS 支持使用[组托管服务帐户](../../../security/group-managed-service-accounts/group-managed-service-accounts-overview.md) \( gMSA \) 作为服务帐户。  这是建议的选项，因为它不再需要在一段时间内管理服务帐户密码。  本文档介绍使用传统服务帐户的另一种情况，例如在仍运行 Windows Server 2008 R2 或更早的域功能级别 DFL 的域中 \( \) 。

> [!NOTE]  
> 你只能针对整个联合服务器场执行一次此过程中的任务。 以后，当你使用 AD FS 联合服务器配置向导创建联合服务器时，必须在场中每台联合服务器上的 **“服务帐户”** 向导页中指定与此相同的帐户。  
  
#### <a name="create-a-dedicated-service-account"></a>创建一个专用服务帐户  
  
1.  \/在位于标识提供程序组织中的 Active Directory 林中创建专用用户服务帐户。 此帐户是 Kerberos 身份验证协议在服务器场方案中工作所必需的，并且允许 \- 在每个联合服务器上通过身份验证。 此帐户仅用于联合服务器场。  
  
2.  编辑用户帐户属性，并选中“密码永不过期”**** 复选框。 这一操作确保此服务帐户的功能不会因为域密码更改要求而被中断。  
  
    > [!NOTE]  
    > 为此专用帐户使用网络服务帐户将会在通过 Windows 集成身份验证尝试访问时导致随机失败，因为 Kerberos 票证不能从一台服务器到另一台服务器上进行验证。  
  
#### <a name="to-set-the-spn-of-the-service-account"></a>设置服务帐户的 SPN  
  
1.  因为 AD FS AppPool 的应用程序池标识作为域用户 \/ 服务帐户运行，所以必须 \( \) 使用 Setspn.exe 命令行工具在域中为该帐户配置服务主体名称 SPN \- 。 默认情况下，Setspn.exe 安装在运行 Windows Server 2008 的计算机上。 在加入用户服务帐户所在的同一个域的计算机上运行以下命令 \/ ：  
  
    ```  
    setspn -a host/<server name> <service account>  
    ```  
  
    例如，在以下方案中，所有联合服务器都群集在域名系统 \( DNS \) 主机名 fs.fabrikam.com 下，并且分配给 AD FS AppPool 的服务帐户名称名为 adfs2farm，请按如下所示键入命令，然后按 enter：  
  
    ```  
    setspn -a host/fs.fabrikam.com adfs2farm  
    ```  
  
    有必要为此帐户只完成一次该任务。  
  
2.  将 AD FS AppPool 标识更改为服务帐户后，将 SQL Server 数据库上的访问控制列表 \( acl 设置 \) 为允许读取此新帐户，以便 AD FS AppPool 可以读取策略数据。  
  
