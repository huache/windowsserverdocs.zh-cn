---
ms.assetid: 330c7b61-dde0-432f-9b74-d250ad9cc808
title: 在页面说明中添加签名\-
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 8d3cc69bde1c9126f97926802b53d049ed1ef501
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859990"
---
# <a name="add-sign-in-page-description"></a>在页面说明中添加签名\-


## <a name="to-add-sign-in-page-description"></a>在页面说明中添加符号\-  
若要将页面说明中的签名\-添加到页面的 "签名"\-，请使用以下 Windows PowerShell cmdlet 和语法。  

![添加登录说明](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

    Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>" 
 
  
> [!IMPORTANT]  
> `SignInPageDescriptionText` 参数的字符串同时支持带标记和不带标记的纯 HTML。 因此，你还可以运行以下 cmdlet 而无需使用 &lt;p&gt; 标记。  `Set-AdfsGlobalWebContent -SignInPageDescriptionText "Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information." ` 

自定义页面中的 "符号\-" 后，将优先使用自定义;因此，你应该为你想要支持的所有语言进行自定义。 所有自定义的内容都使用区域设置参数。 配置本地化内容时，应将其配置为在配置国家和地区之前\-较小的区域设置，例如 "en"，\-特定的区域设置，例如 "en\-us"。  

## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)  
