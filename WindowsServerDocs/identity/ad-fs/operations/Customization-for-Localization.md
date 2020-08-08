---
ms.assetid: 38bbc002-a8fa-4211-9328-4ef67fca0acf
title: 本地化自定义
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 41a540b43fde264718ca7aa81ba0e48184cf1265
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956384"
---
# <a name="customization-for-localization"></a>本地化自定义

可以将 Web 内容本地化为英语以外的语言。 当你在本地化时，请注意以下事项。

自定义内容后，将优先该自定义；因此，你应该为你想要支持的所有语言进行自定义。 所有自定义的内容都使用区域设置参数。 在配置本地化内容时，请先使用国家/地区的 \- 区域设置，例如 "en"，然后再配置国家和地区特定的 \- 区域设置，例如 "en-us" \- 。

下面显示了一些其他代码示例。

```powershell
Set-AdfsWebTheme -TargetName default -Logo @{Locale="";Path="c:\contoso.png"}
Set-AdfsWebTheme -TargetName default -Illustration @{Locale="";Path="c:\illustration.png"}
```

下面显示了一些其他代码示例。

```powershell
Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" –locale "en"

Set-AdfsGlobalWebContent -ErrorPageDescriptionText "Il s'agit de description de page erreur de Contoso" –locale "fr"
```

如果要将 web 内容自定义为英语之外的其他语言，则建议使用 Windows PowerShell ISE。 有关其他信息，请参阅[介绍 Windows PowerShell ISE](/previous-versions/mt707506(v=msdn.10))。

## <a name="additional-references"></a>其他参考

[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)
