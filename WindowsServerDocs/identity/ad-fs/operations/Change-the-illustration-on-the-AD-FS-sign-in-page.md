---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: 在 AD FS 登录页上更改图例
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 47a71fffc864f6ae5ecb46d562f92d2d9cece092
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519786"
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>在 AD FS 登录页上更改图例

## <a name="change-the-illustration"></a>更改图例

若要更改图例，请在 "登录" 页上显示的左侧图形， \- 使用以下 Windows PowerShell cmdlet 和语法。

![更改图示](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

> [!IMPORTANT]
> 我们建议图片的尺寸为 1420 x 1080 像素 (96 DPI)，且文件大小不应超过 200 KB。

```powershell
Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}
```

## <a name="additional-references"></a>其他参考

[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)
