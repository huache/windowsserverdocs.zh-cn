---
title: 对于更大部署的支持
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 07d0c4c6-3e92-4969-82b8-105e46ab8d97
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: bf5b6027c934c1dec9916ff08995a7f096a2b8bd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622442"
---
# <a name="support-for-larger-deployments"></a>对于更大部署的支持

>适用于： Windows Server 2016 Essentials

> [!IMPORTANT]
> 本主题中所述的功能仅适用于启用了 Essentials Experience 角色的 Windows Server 2016，而不适用于 Windows Server 2016 Essentials SKU。


Windows Server Essentials 现在支持较大的部署，其中包括：

- 多个域
- 多个域控制器
- 指定指定域控制器的能力
- 最多支持500用户和500设备

## <a name="support-for-multiple-domains"></a>支持多个域

Windows server 2012 R2 Essentials 只支持每个服务器一个域，这是必需的，并且 Essentials 服务器必须是林的根。 尽管仍需要域和林，但现在可以将 Windows Server 2016 Essentials 体验角色部署在 Windows Server 2016 Standard 或 Datacenter 上，以支持多个域。

## <a name="support-for-multiple-domain-controllers"></a>支持多个域控制器

 Windows Server Essentials 2012 R2 会阻止利用 Azure Active Directory 的任何服务，如 Microsoft 365，其中部署了多个域控制器。 原因是本地域控制器与 Azure Active Directory 之间的帐户和密码同步可能会导致帐户凭据包含不同步的密码。此限制已在 Windows Server 2016 Essentials 中删除。

## <a name="ability-to-specify-a-designated-domain-controller"></a>指定指定域控制器的能力

你现在可以选择一个指定的域控制器，它将缩短 Active Directory 域对象的检索时间，并协调域中其他域控制器的帐户更改同步。

默认指定的域控制器将与运行 Windows Server Essentials Experience 服务器角色的服务器相同。 如果该服务器是成员服务器，这意味着它不是域控制器，则根据测试域中的域控制器与运行 Windows Server Experience Server 角色的服务器的网络延迟最低，将自动确定默认的指定域控制器。 如果要手动更改哪个服务器是指定的域控制器，可以在**Windows Server Essentials 仪表板**的 "**设置**" 中执行此操作，如下所示。

![屏幕截图显示前台和 Windows Server Essentials 仪表板中的 "设置" "控制面板"。 "设置" 控制面板的 "指定的域控制器" 页当前处于选中状态。](media/larger-deployments-1.PNG)

## <a name="support-for-500-users-and-500-devices"></a>支持500用户和500设备
-------------------------------------

Windows Server 2012 R2 Essentials 中受支持的用户和设备的最大数量分别为25和50。 随着 Windows Server Essentials Experience 服务器角色的引入，此限制增加到了100用户和200设备。

Windows Server 2016 Essentials 支持500用户和500设备。 这样做可能是对提供程序框架和对象列表控件的更新，以便它们缓存并快速呈现大型用户和设备对象列表。 此外，还添加了搜索和筛选功能，可快速查找你可能正在查找的用户或设备 (参见图 5-2) 。 你将在 **Windows Server Essentials 仪表板**、 **远程 Web 访问**、Windows 和 Windows Phone 存储 **我的服务器** 应用程序中找到搜索和筛选功能。

![显示使用 Windows Server Essentials 仪表板的搜索功能以搜索字符串 "d5c" 的屏幕截图。 此搜索的结果包括两个文件和文件夹，以及两个用户。](media/larger-deployments-2.PNG)

显示使用 Windows Server Essentials 仪表板的搜索功能以搜索字符串 "d5c" 的屏幕截图。 此搜索的结果包括两个文件和文件夹，以及两个用户。

> [!NOTE]
> 当 Windows Server Essentials 服务器角色的支持用户和设备限制增加时，支持的客户端备份限制将保留在75。

<a name="see-also"></a>请参阅
--------
[Windows Server Essentials 入门](get-started.md)