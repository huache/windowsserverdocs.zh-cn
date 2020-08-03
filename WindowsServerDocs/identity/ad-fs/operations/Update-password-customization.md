---
ms.assetid: 7e804590-6d6c-4cca-ac14-02d4dff06cec
title: 更新密码自定义
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 42131ef5e149c62dd5449d8ada196b1068fd30ac
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519716"
---
# <a name="update-password-customization"></a>更新密码自定义

在某些情况下，用户可能无法连接到企业网络来更改其帐户密码。 此因素可能会产生问题，尤其对于那些可能离最近的企业办公室都较远的远程员工。 对于这些特定情况，只有通过连接到 Internet 才能使用更新密码页面。

通过提供自己的页面描述，你可以自定义更新密码页。

若要启用密码更新页面，请转到“终结点”下的“AD FS 管理”。 更新密码的终结点位于底部，在“其他 - /adfs/portal/updatepassword/”下。 一旦启用了该终结点，则必须重新启动 AD FS 服务。 必须手动完成此操作。 如果希望在外部使用 "更新密码" 网页，并使用 Web 应用程序代理，则需要在代理上启用它（在代理上启用）。 然后，你可以 `https://<fqdn>/adfs/portal/updatepassword/` 在加入工作区的设备上导航到，你应该会看到 "更新密码" 页。

![更新](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom5.png)

## <a name="customize-the-update-password-page-description"></a>自定义更新密码页面描述

若要自定义更新密码页面描述，请使用以下 Windows PowerShell cmdlet 和语法。

```powershell
Set-AdfsGlobalWebContent -UpdatePasswordPageDescriptionText "This is the Contoso Update Password page."
```

## <a name="additional-references"></a>其他参考

[AD FS 用户登录自定义](AD-FS-user-sign-in-customization.md)
