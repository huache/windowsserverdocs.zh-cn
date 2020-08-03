---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: 在 AD FS 登录页上更改公司徽标
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b61f7321dc75613a3450998284536673bd790f2b
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519816"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>在 AD FS 登录页上更改公司徽标

## <a name="change-company-logo"></a>更改公司徽标

若要更改 "登录" 页上显示的公司徽标 \- ，请使用以下 PowerShell Windows powershell cmdlet 和语法。

![更改徽标](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

> [!IMPORTANT]
> 我们建议徽标的尺寸为 260 x 35 (96 DPI)，且文件大小不应超过 10 KB。

```powershell
Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}
```

> [!NOTE]
> `TargetName` 参数是必需的。 用 AD FS 发布的默认主题名为*default*。

## <a name="additional-references"></a>其他参考

[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)
