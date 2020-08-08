---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: AD FS 登录页的高级自定义
author: billmath
ms.author: billmath
manager: femila
ms.date: 01/16/2019
ms.topic: article
ms.openlocfilehash: dd0fa97024f286d90f096da9fa132f40c1a78aae
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956664"
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>AD FS 登录页的高级自定义


## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>AD FS 登录页的高级自定义 \-
Windows Server 2012 R2 中的 AD FS \- 为自定义登录体验提供内置支持 \- 。 大多数情况下，内置的 \- Windows PowerShell cmdlet 都是必需的。  建议你尽可能使用内置的 \- Windows PowerShell 命令自定义标准元素，以便 AD FS 登录 \- 体验。  有关详细信息，请参阅[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)。

在某些情况下，AD FS 管理员可能希望提供附加的登录 \- 体验，而不能通过 AD FS 附带的现有 PowerShell 命令来实现 \- 。 在某些情况下，在下面提供的准则中是可行的， \( \) 管理员可以 \- 通过将其他逻辑添加到 AD FS 提供的**onload.js** ，并在所有 AD FS 页上执行，从而进一步自定义登录体验。

## <a name="things-to-know-before-you-start"></a>开始之前要了解的问题

-   不支持影响重定向流或修改 AD FS 使用的协议参数的任何更改。

-   默认 web 主题附带的原始 onload.js 包含处理不同窗体规格的页面呈现的代码。 建议不要修改原始 onload.js 内容，而只是将代码追加到处理自定义逻辑的现有 onload.js。

-   AD FS 附带了一个 \- 名为 Default 的内置 web 主题。 你无法修改默认 web 主题的 onload.js。 若要更新 onload.js，必须创建并使用自定义 web 主题 AD FS 登录 \- 页。  有关如何创建自定义 web 主题的信息，请参阅[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)。

-   相同的 onload.js 将在所有 ADFS 页面上执行（ \( 例如 基于窗体 \- 的登录页、主页领域发现页等。 \) 需要确保脚本中的代码仅在设计时才执行，并且不会意外执行。

-   引用任何 HTML 元素时，确保在对元素执行操作之前始终检查元素是否存在。 这将提供稳定性并确保不在不包含此元素的页上执行自定义逻辑。 只需在 AD FS 登录页上查看 HTML 源 \- 即可查看现有元素。

-   强烈建议在备用环境中验证自定义，并在将其放入生产 AD FS 服务器之前对其进行测试。 这会降低最终用户在验证之前向这些自定义项公开的几率。

## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>使用 onload.js 自定义 AD FS 登录 \- 体验
自定义 AD FS 服务的 onload.js 时，请使用以下步骤。

#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>自定义 AD FS 服务的 onload.js

1.  若要将自定义逻辑添加到 onload.js，需要首先创建自定义 web 主题。 出厂时提供的主题 \- \- \- 称为 "默认主题"。 可以导出并使用该默认主题，以便可以快速启动。 以下 cmdlet 将创建一个自定义 web 主题，该主题将复制默认 web 主题：

    ```
    New-AdfsWebTheme –Name custom –SourceName default

    ```

2.  然后，你可以导出自定义或默认 web 主题以获取 onload.js 文件。 若要导出 web 主题，请使用以下 cmdlet：

    ```
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme

    ```

    你将在上述导出 cmdlet 中指定的目录下的脚本文件夹中找到 onload.js，并将你的自定义逻辑添加到脚本中， \( 请参阅以下示例部分中的用例 \) 。

3.  进行必要的修改以根据你的需要自定义 onload.js。

4.  用修改后的 onload.js 更新主题。 使用以下 cmdlet 将更新 onload.js 应用到自定义 web 主题：

     对于 Windows Server 2012 R2 上的 AD FS：

    ```
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';path="c:\theme\script\onload.js"}

    ```
    对于 Windows Server 2016 上的 AD FS：

     ```
    Set-AdfsWebTheme -TargetName custom -OnLoadScriptPath "c:\theme\script\onload.js"

    ```

5.  若要将自定义 web 主题应用到 AD FS，请使用以下 cmdlet：

    ```
    Set-AdfsWebConfig -ActiveThemeName custom
    ```

## <a name="additional-customization-examples"></a>其他自定义示例
下面是添加到 onload.js 中的自定义代码的示例，用于实现不同的微调 \- 目的。 添加自定义代码时，请始终将自定义代码追加到 onload.js 的底部。

### <a name="example-1-change-sign-in-with-organizational-account-string"></a>示例1：更改 "用组织帐户登录" 字符串
AD FS 默认的 "基于窗体的 \- 登录 \- " 页的标题为 "使用组织帐户登录"。

如果要将此字符串替换为自己的字符串，可以将以下代码添加到 onload.js。

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

### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>示例2： \- 在基于 AD FS 窗体的 \- 登录页上，接受 SAM 帐户名作为登录格式 \-
默认 AD FS 基于窗体的 \- 登录 \- 页支持用户主体名称 upn 的登录 \( 格式 \) \( （例如） <strong>johndoe@contoso.com</strong> \) 或域限定 sam \- 帐户名称 \( **contoso \\ johndoe**或**contoso.com \\ johndoe** \) 。 如果你的所有用户都来自同一个域，并且他们仅知道 sam \- 帐户名称，你可能想要支持用户只能使用 sam 帐户名称登录的方案 \- 。 你可以将以下代码添加到 onload.js 以支持此方案，只需将以下示例中的域 "contoso.com" 替换为要使用的域。

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


