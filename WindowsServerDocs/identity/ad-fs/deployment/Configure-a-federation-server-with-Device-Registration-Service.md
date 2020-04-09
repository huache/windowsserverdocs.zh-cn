---
ms.assetid: fdd1c1fd-55aa-4eb8-ae84-53f811de042c
title: 使用设备注册服务配置联合服务器
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: c7775801940faeba07ad91aa81434a34c97eb6bc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855510"
---
# <a name="configure-a-federation-server-with-device-registration-service"></a>使用设备注册服务配置联合服务器

完成[步骤4：配置联合服务器](https://technet.microsoft.com/library/dn303424.aspx)中的步骤后，你可以在联合服务器上 \(DRS\) 启用设备注册服务。 设备注册服务为无缝第二重身份验证提供了一种载入机制、\(SSO\)上的永久单一登录\-，以及需要访问公司资源的使用者的条件性访问。 有关 DRS 的详细信息，请参阅[跨公司应用程序从任何设备加入工作区以实现 SSO 和无缝第二重身份验证](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)  
  
## <a name="prepare-your-active-directory-forest-to-support-devices"></a>准备 Active Directory 林以提供设备支持  
  
> [!NOTE]  
> 这是一个\-时间操作，你必须运行该操作来准备 Active Directory 林以支持设备。 若要完成此过程，你必须使用企业管理员权限登录，并且 Active Directory 林必须具有 Windows Server 2012 R2 架构。  
>   
> 此外，DRS 要求林根域中至少有一个全局编录服务器。 需要全局编录服务器才能在 AD FS 身份验证过程中运行 Initialize\-Initialize-addeviceregistration 和。 AD FS 在每个身份验证请求上初始化 DRS config 对象的\-内存表示形式，并且如果在当前域中的 DC 上找不到 DRS 配置对象，则将尝试对在初始化\-Initialize-addeviceregistration 过程中对 DRS 对象进行设置的 GC 进行请求。  
  
#### <a name="to-prepare-the-active-directory-forest"></a>准备 Active Directory 林  
  
1.  在联合服务器上，打开 Windows PowerShell 命令窗口并键入：  
  
    ```  
    Initialize-ADDeviceRegistration  
    ```  
  
2.  在出现“ServiceAccountName”提示时，输入你选择用作 AD FS 服务帐户的服务帐户名。  如果这是一个 gMSA 帐户，请在域中输入帐户 **\\accountname $** 格式。 对于域帐户，请使用 format **domain\\accountname**。  
  
## <a name="enable-device-registration-service-on-a-federation-server-farm-node"></a>启用联合服务器场节点上的设备注册服务  
  
> [!NOTE]  
> 必须以域管理员权限登录才能完成此过程。  
  
#### <a name="to-enable-device-registration-service"></a>启用设备注册服务  
  
1.  在联合服务器上，打开 Windows PowerShell 命令窗口并键入：  
  
    ```  
    Enable-AdfsDeviceRegistration  
    ```  
  
2.  在 AD FS 场中的每个联合场节点上重复此步骤。  
  
## <a name="enable-seamless-second-factor-authentication"></a>启用无缝第二重身份验证  
无缝第二重身份验证是 AD FS 中的一项增强功能，可为企业资源和应用程序的访问权限提供额外的保护级别，这些资源和来自尝试访问它们的外部设备。 当个人设备加入工作区时，它将成为 "已知" 设备，管理员可以使用此信息来驱动条件访问和对资源的入口访问。  
  
#### <a name="to-enable-seamless-second-factor-authentication-persistent-single-sign-on-sso-and-conditional-access-for-workplace-joined-devices"></a>若要启用无缝第二重身份验证，\(SSO\) 上的永久单一签名\-和加入工作区的设备的条件访问  
  
1.  在 AD FS 管理控制台中，导航到 "身份验证策略"。 选择“编辑全局主要身份验证”。 选中“启用设备身份验证”旁边的复选框，然后单击“确定”。  
  
## <a name="update-the-web-application-proxy-configuration"></a>更新 Web 应用程序代理配置  
  
> [!IMPORTANT]  
> 不需要将设备注册服务发布到 Web 应用程序代理。  在联合服务器上启用设备注册服务后，该服务将通过 Web 应用程序代理提供。  如果 Web 应用程序代理配置是在启用设备注册服务之前部署的，则可能需要完成此过程以更新它。  
  
#### <a name="to-update-the-web-application-proxy-configuration"></a>更新 Web 应用程序代理配置  
  
1.  在您的 Web 应用程序代理服务器上，打开 Windows PowerShell 命令窗口并键入  
  
    ```  
    Update-WebApplicationProxyDeviceRegistration  
    ```  
  
2.  当系统提示输入凭据时，请输入对联合服务器具有管理权限的帐户的凭据。  
  
## <a name="see-also"></a>另请参阅 

[AD FS 部署](../../ad-fs/AD-FS-Deployment.md)  

[Windows Server 2012 R2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[部署联合服务器场](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

