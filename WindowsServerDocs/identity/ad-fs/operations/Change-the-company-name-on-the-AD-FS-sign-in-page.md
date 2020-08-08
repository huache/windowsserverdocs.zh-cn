---
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: 在 AD FS 登录页上更改公司名称
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: e47d0ee6b1969bca847dd88bfc6cca69bd72b6ba
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956574"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>在 AD FS 登录页上更改公司名称

若要更改 "登录" 页上显示的公司名称 \- ，请使用以下 Windows PowerShell cmdlet 和语法。 默认情况下，通过使用在安装期间输入的联合身份验证服务显示名称中的值设置此值。

![更改名称](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)

```powershell
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"
```

> [!NOTE]
> 你还可以使用 Windows PowerShell 集成脚本环境 \( ISE \) 来更改公司名称。 通过使用 Windows PowerShell ISE，你可以在符合 Unicode 的环境中显示内容 \- 。 有关其他信息，请参阅 [Windows PowerShell ISE 简介](/previous-versions/mt707506(v=msdn.10))。

## <a name="additional-references"></a>其他参考

- [AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)
