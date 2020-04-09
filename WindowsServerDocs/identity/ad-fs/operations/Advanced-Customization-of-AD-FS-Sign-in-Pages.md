---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: AD FS 登录页的高级自定义
author: billmath
ms.author: billmath
manager: femila
ms.date: 01/16/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ea149e6b9a5fbf5c0671991a61f9bcda35656022
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859980"
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>AD FS 登录页的高级自定义

  
## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>页面中 AD FS 登录\-的高级自定义  
Windows Server 2012 R2 中的 AD FS 提供了针对自定义签名\-的内置\-支持。 在大多数情况下，Windows PowerShell cmdlet 中生成的\-都是必需的。  建议使用 Windows PowerShell 命令中的生成\-自定义标准元素，以便尽可能 AD FS 签名\-。  有关详细信息，请参阅[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)。  
  
在某些情况下，AD FS 管理员可能希望通过 AD FS\-框中提供的现有 PowerShell 命令提供额外的签名\-。 在某些情况下，可以在下面提供的准则中 \(可行\) 以便管理员通过将其他逻辑添加到由 AD FS 提供并在所有 AD FS 页上执行的**方法来进一步**自定义签名\-。  
  
## <a name="things-to-know-before-you-start"></a>开始之前要了解的问题  
  
-   不支持影响重定向流或修改 AD FS 使用的协议参数的任何更改。
  
-   作为默认 web 主题附带的 "初始 onload" 包含处理不同窗体规格的页面呈现的代码。 建议不要修改原始 onload 内容，而只是将代码追加到处理自定义逻辑的现有 onload。  
  
-   AD FS 附带了一个名为 Default 的 web 主题中的内置\-。 你无法修改默认 web 主题的 onload。 若要更新 onload，必须创建并使用自定义 web 主题，以便在页面中 AD FS 的\-。  有关如何创建自定义 web 主题的信息，请参阅[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)。  
  
-   \(ex，同一 onload 将在所有 ADFS 页面上执行。 表单\-基于登录页面、主领域发现页面等\)。 需要确保脚本中的代码仅在设计时才执行，并且不会意外执行。  
  
-   引用任何 HTML 元素时，确保在对元素执行操作之前始终检查元素是否存在。 这将提供稳定性并确保不在不包含此元素的页上执行自定义逻辑。 只需在页面上的 AD FS sign\-上查看 HTML 源即可查看现有元素。  
  
-   强烈建议在备用环境中验证自定义，并在将其放入生产 AD FS 服务器之前对其进行测试。 这会降低最终用户在验证之前向这些自定义项公开的几率。  
  
## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>使用 onload 自定义 AD FS sign\-体验  
为 AD FS 服务自定义 onload 时，请执行以下步骤。  
  
#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>为 AD FS 服务自定义 onload  
  
1.  若要将自定义逻辑添加到 onload，需要首先创建自定义 web 主题。 \-box\-\-提供的主题称为 "默认"。 可以导出并使用该默认主题，以便可以快速启动。 以下 cmdlet 将创建一个自定义 web 主题，该主题将复制默认 web 主题：  
  
    ```  
    New-AdfsWebTheme –Name custom –SourceName default  
  
    ```  
  
2.  然后，你可以导出自定义或默认 web 主题，以获取 onload 文件。 若要导出 web 主题，请使用以下 cmdlet：  
  
    ```  
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  
  
    ```  
  
    你将在上述导出 cmdlet 中指定的目录下的脚本文件夹中找到 onload，并将你的自定义逻辑添加到脚本 \(参见下面的 "示例" 部分中的用例\)。  
  
3.  进行必要的修改以根据你的需要自定义 onload。  
  
4.  用修改的 onload 更新主题。 使用以下 cmdlet 将更新 onload 应用到自定义 web 主题：  

     对于 Windows Server 2012 R2 上的 AD FS：  

    ```  
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';path="c:\theme\script\onload.js"}  
  
    ```  
    对于 Windows Server 2016 上的 AD FS：

     ```  
    Set-AdfsWebTheme -TargetName custom -OnLoadScriptPath "c:\ADFStheme\script\onload.js"   
  
    ```  
  
5.  若要将自定义 web 主题应用到 AD FS，请使用以下 cmdlet：  
  
    ```  
    Set-AdfsWebConfig -ActiveThemeName custom  
    ```  
  
## <a name="additional-customization-examples"></a>其他自定义示例  
下面是添加到 onload 的自定义代码示例，用于\-优化目的。 添加自定义代码时，请始终将自定义代码附加到 onload 的底部。  
  
### <a name="example-1-change-sign-in-with-organizational-account-string"></a>示例1：更改 "用组织帐户登录" 字符串  
页面上的默认 AD FS 窗体中\-的签名\-的标题为 "使用组织帐户登录"。  
  
如果要将此字符串替换为自己的字符串，可将以下代码添加到 onload。  
  
```  
// Sample code to change "Sign in with organizational account" string.  
  
// Check whether the loginMessage element is present on this page.  
var loginMessage = document.getElementById('loginMessage');  
if (loginMessage)  
{  
       // loginMessage element is present, modify its properties.  
       loginMessage.innerHTML = 'Your company description text';  
}  
  
```  
  
### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>示例2：作为 AD FS 窗体上的登录格式，接受 SAM\-帐户名\-\-页码  
页面上的默认 AD FS 窗体中的 "基于\-的签名\-" 支持 Upn\) \(<strong>johndoe@contoso.com\) 或</strong>域限定 sam\-帐户名称 \(**contoso\\johndoe**或**contoso.com\\johndoe**\)的登录 \(格式。 如果你的所有用户都来自同一个域，并且他们仅了解 sam\-帐户名称，你可能想要支持这样的方案：用户仅能使用其登录\-帐户名称。 你可以将以下代码添加到 onload 以支持此方案，只需将以下示例中的域 "contoso.com" 替换为你想要使用的域。  
  
```  
if (typeof Login != 'undefined'){  
    Login.submitLoginRequest = function () {   
    var u = new InputUtil();  
    var e = new LoginErrors();  
    var userName = document.getElementById(Login.userNameInput);  
    var password = document.getElementById(Login.passwordInput);  
    if (userName.value && !userName.value.match('[@\\\\]'))   
    {  
        var userNameValue = 'contoso.com\\' + userName.value;  
        document.forms['loginForm'].UserName.value = userNameValue;  
    }  
  
    if (!userName.value) {  
       u.setError(userName, e.userNameFormatError);  
       return false;  
    }  
  
    if (!password.value)   
    {  
        u.setError(password, e.passwordEmpty);  
        return false;  
    }  
    document.forms['loginForm'].submit();  
    return false;  
};  
}  
  
```  
  
## <a name="additional-references"></a>其他参考 
[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)  
  

