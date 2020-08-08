---
title: Azure AD UX Web 主题 AD FS
description: 以下文档介绍如何更改 AD FS 窗体登录，使其类似于 Azure AD 的用户体验。
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/24/2017
ms.topic: article
ms.openlocfilehash: a7cb3a037d074fc4a61e6c805bca181316643bb3
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956674"
---
# <a name="using-an-azure-ad-ux-web-theme-in-active-directory-federation-services"></a>在 Active Directory 联合身份验证服务中使用 Azure AD UX Web 主题
目前 AD FS 窗体登录不会镜像 Azure/O365 登录体验。  为了向最终用户提供更统一且无缝的体验，我们发布了以下可应用到 AD FS 服务器的级联样式表 web 主题。  目前，Windows Server 2016 上的 AD FS 窗体登录如下所示：

![当前登录](media/Azure-UX-Web-Theme-in-AD-FS/one.png)


利用新的样式表，用户体验将类似于 Azure 和 Office 365 登录体验。

## <a name="download-the-css-style-sheet"></a>下载 CSS 样式表
你可以从以下 Github[位置](https://github.com/Microsoft/adfsWebCustomization/tree/master/centeredUi)下载 web 主题。


## <a name="enabling-the-new-web-theme"></a>启用新的 web 主题
若要启用新的 web 主题，请使用以下过程：

### <a name="to-enable-the-new-azure-ad-ux-web-theme-in-ad-fs"></a>若要启用新的 Azure AD UX web 主题 AD FS
1. 以管理员身份启动 PowerShell
2. 使用 PowerShell 创建新的 web 主题：`New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"}`
3. 使用 powershell 将新主题设置为活动主题： `Set-AdfsWebConfig -ActiveThemeName custom` 
    ![ powershell](media/Azure-UX-Web-Theme-in-AD-FS/two.png)
4. 转到 https:// <AD FS name.domain> /adfs/ls/idpinitiatedsignon.htm 登录来测试登录 ![](media/Azure-UX-Web-Theme-in-AD-FS/three.png)

> !纪录你需要确保 idpinitiatedsignon.aspx 已启用。  默认情况下不启用该日志。  若要启用 idpinitiatedsignon.aspx，请使用以下 PowerShell 命令：`Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## <a name="image-recommendations"></a>映像建议
启用居中的 UI 使你可以使用相同的背景和徽标图像 Azure Active Directory 公司品牌。 通常，相同的大小、比率和格式建议也适用。

### <a name="logo"></a>徽标

描述 | 约束 | 建议
------- | ------- | ----------
徽标显示在登录面板的顶部。 | 透明 JPG 或 PNG<br>最大高度：36 px<br>最大宽度：245 px | 在此处使用组织的徽标。<br>使用透明图像。 不要假设背景为白色。<br>请勿在映像中的徽标周围添加填充，否则徽标看起来会很小。

### <a name="background"></a>背景

描述 | 约束 | 建议
------- | ------- | ----------
此选项显示在登录页的背景中，定位在可视空间的中心，并可通过缩放和裁剪来适应浏览器窗口。    <br>在诸如手机这类窄屏上，将不会显示此图像。<br>当页面加载时，将对此图像应用一个不透明度为 0.55 的黑色蒙板。 | JPG 或 PNG<br>图像尺寸：1920x1080 px<br>文件大小：&lt; 300 KB | <br>在没有鲜明主题的位置处使用图像。 不透明的登录窗体出现在此图像的中心之上，可以覆盖图像的任何部分，具体取决于浏览器窗口的大小。<br>请使该文件保持较小，以确保快速加载。

## <a name="next-steps"></a>后续步骤
- [Windows Server 2016 中的 AD FS 自定义](./ad-fs-customization-in-windows-server.md)
- [高级自定义](Advanced-Customization-of-AD-FS-Sign-in-Pages.md)
- [自定义 web 主题](Custom-Web-Themes-in-AD-FS.md)
