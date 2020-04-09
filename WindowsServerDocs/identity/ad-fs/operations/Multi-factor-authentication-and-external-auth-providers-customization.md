---
title: 多重身份验证和外部身份验证提供程序自定义
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.assetid: 08724d45-9be4-4c56-a5f1-2cf40864e136
ms.technology: identity-adfs
ms.openlocfilehash: 8252244738d59f11a07c3bebadbbf2a5f4818845
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816230"
---
# <a name="multi-factor-authentication-and-external-authentication-providers-customization"></a>多重身份验证和外部身份验证提供程序自定义 



在 AD FS 中，提供对多重身份验证的支持\-\-"\-" 框。 例如，你可以将 AD FS 配置为使用证书身份验证中的内置\-作为第二因素身份验证。 此外还可以使用外部身份验证提供程序。 这种方法可以使 AD FS 与其他服务（如 Azure 多重身份验证）集成，也可以开发自己的提供程序。 有关如何使用 AD FS 注册外部身份验证提供程序的详细信息，请参阅[解决方案指南：使用多\-因素访问控制管理风险](https://technet.microsoft.com/library/dn280937.aspx)。  
  
建议外部身份验证提供程序使用 AD FS 提供的 css 文件中定义的类来创作身份验证 UI。 可以使用以下 cmdlet 导出默认 Web 主题，并检查用户界面类和 .css 文件中定义的元素。 Css 文件可用于在外部身份验证提供程序的用户界面中开发符号\-。  
  

    Export-AdfsWebTheme -Name default -DirectoryPath C:\theme  
 
  
下面是用户界面中的符号\-的示例，由外部身份验证提供程序以红色突出显示。 用户界面使用 AD FS .css 文件中的 UI 类。  
  
![AD FS 和 MFA](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom8.png)  
  
编写新的自定义身份验证方法之前，我们建议你先研究 AD FS 主题和样式定义，以了解内容创作要求。  
  
-   自定义身份验证方法只是在页面而不是完整页面上的 AD FS sign\-上创作 HTML 段。 应使用 AD FS 的样式定义来获得一致的外观和行为。  
  
![AD FS 和 MFA](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom9.png)  
  
-   请注意，AD FS 管理员可以自定义 AD FS 样式。 . 我们不建议对你自己的样式进行硬编码。 相反，我们建议尽可能使用 AD FS 样式。  
  
-   \-"\-" 框中，将用一个左\-创作 AD FS 样式，以\-向右 \(RTL\) 样式，并向右\-\-RTL \(RTL\)。 管理员可以自定义这两个，并可以通过 web 主题定义\-特定样式提供语言。 每个样式表都具有三个部分及其各自的备注：  
  
    -   **主题样式**\- 这些样式不应且不能使用。 这些样式是为了在所有页面上定义主题。 它们由元素 ID 特意定义，以便不会重新使用这些样式。  
  
    -   **常用样式**\- 这些是应该用于你的内容的样式。  
  
    -   外形**规格样式**\- 这些是不同形式因素的样式。 你应该了解此部分以确保你的内容能够适应不同的外形因素，例如手机和平板电脑。  
  
有关其他信息，请参阅[解决方案指南：使用多\-因素访问控制管理风险](https://technet.microsoft.com/library/dn280937.aspx)和[解决方案指南：使用适用于敏感应用程序的附加\-多因素身份验证管理风险](https://tnstage.redmond.corp.microsoft.com/library/dn280949.aspx)。  

## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md) 
