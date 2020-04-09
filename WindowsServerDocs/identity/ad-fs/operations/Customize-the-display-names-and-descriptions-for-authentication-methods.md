---
ms.assetid: 309d6358-777d-496a-856d-728246c7d9a1
title: 为身份验证方法自定义显示名称和说明
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 218643bbd5ada63b6bee2b91a7bace3f9959c0bd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816440"
---
# <a name="customize-the-display-names-and-descriptions-for-authentication-methods"></a>为身份验证方法自定义显示名称和说明 


若要为身份验证方法自定义显示名称和说明，可以使用 `Set-AdfsAuthenticationProviderWebContent` PowerShell cmdlt。  若要使用此 cmdlt，你必须首先获取要自定义的身份验证方法的名称。  这可以使用 `Get-AdfsGlobalAuthenticationPolicy`来进行。  在下面的示例中，我们看到，在页的 sign\-上，显示以下内容： "使用 x.509 证书登录"。  我们要为我们的用户简化此操作。  
  
![自定义 displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update1.PNG)  
  
因此我们首先获取身份验证方法的名称，然后编辑显示的文本。  
  
 
    Get-AdfsGlobalAuthenticationPolicy  
      
    AdditionalAuthenticationProvider  : {}  
    DeviceAuthenticationEnabled   : False  
    PrimaryIntranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    PrimaryExtranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    WindowsIntegratedFallbackEnabled  : True  
      
    Set-AdfsAuthenticationProviderWebContent -Name CertificateAuthentication -DisplayName "Sign in with a certificate"  
  
  
![自定义 displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update2.PNG)  
  
现在我们可以看到显示消息已更改。  
  
![自定义 displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update3.PNG)  

## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md) 
