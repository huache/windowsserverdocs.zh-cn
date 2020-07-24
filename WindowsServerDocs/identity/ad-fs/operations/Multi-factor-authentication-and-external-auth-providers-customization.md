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
ms.openlocfilehash: b7e94264511d1f05871a893b5a62dae4bda16d58
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963809"
---
# <a name="multi-factor-authentication-and-external-authentication-providers-customization"></a>多重身份验证和外部身份验证提供程序自定义 



在 AD FS 中，提供了对多重身份验证的 \- 支持 \- \- 。 例如，你可以将 AD FS 配置为使用内置的 \- 证书身份验证作为第二因素身份验证。 此外还可以使用外部身份验证提供程序。 这种方法可以使 AD FS 与其他服务（如 Azure 多重身份验证）集成，也可以开发自己的提供程序。 请参阅[解决方案指南：使用多重 \- 因素访问控制管理风险](./manage-risk-with-conditional-access-control.md)获取有关如何使用 AD FS 注册外部身份验证提供程序的详细信息。  
  
建议外部身份验证提供程序使用 AD FS 提供的 css 文件中定义的类来创作身份验证 UI。 可以使用以下 cmdlet 导出默认 Web 主题，并检查用户界面类和 .css 文件中定义的元素。 在开发 \- 外部身份验证提供程序的登录用户界面时，可以使用 .css 文件。  
  

    Export-AdfsWebTheme -Name default -DirectoryPath C:\theme  
 
  
下面是登录 \- 用户界面的示例，由外部身份验证提供程序以红色突出显示。 用户界面使用 AD FS .css 文件中的 UI 类。  
  
![AD FS 和 MFA](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom8.png)  
  
编写新的自定义身份验证方法之前，我们建议你先研究 AD FS 主题和样式定义，以了解内容创作要求。  
  
-   自定义身份验证方法仅在 AD FS 登录 \- 页面而不是完整页面上创作 HTML 段。 应使用 AD FS 的样式定义来获得一致的外观和行为。  
  
![AD FS 和 MFA](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom9.png)  
  
-   请注意，AD FS 管理员可以自定义 AD FS 样式。 . 我们不建议对你自己的样式进行硬编码。 相反，我们建议尽可能使用 AD FS 样式。  
  
-   在现成的 \- \- 中，AD FS 样式是用一个从左 \- 到 \- 右的 \( LTR \) 样式和一个从右向 \- 左的 \- \( RTL \) 编写的。 管理员可以自定义这两个，并可以 \- 通过 web 主题定义提供特定于语言的样式。 每个样式表都具有三个部分及其各自的备注：  
  
    -   **主题样式** \-不应且不能使用这些样式。 这些样式是为了在所有页面上定义主题。 它们由元素 ID 特意定义，以便不会重新使用这些样式。  
  
    -   **常用样式** \-这些是应该用于你的内容的样式。  
  
    -   外形**规格样式** \-这些是不同形式因素的样式。 你应该了解此部分以确保你的内容能够适应不同的外形因素，例如手机和平板电脑。  
  
有关其他信息，请参阅[解决方案指南：使用多重 \- 因素访问控制管理风险](./manage-risk-with-conditional-access-control.md)和[解决方案指南：使用 \- 适用于敏感应用程序的附加多重身份验证管理风险](https://tnstage.redmond.corp.microsoft.com/library/dn280949.aspx)。  

## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md) 
