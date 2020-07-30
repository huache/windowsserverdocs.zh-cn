---
title: 管理 Windows Server Essentials 中的 SharePoint Online
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 282f3634-6de6-4691-803c-df6c3c16660d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e75db6f67bfa46bc5980688f82a6b4ebf56eaa0f
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409537"
---
# <a name="manage-sharepoint-online-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的 SharePoint Online

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

如果将 Office 365 与 Windows Server Essentials 服务器集成，则可以从仪表板管理 SharePoint Online 库和团队网站，而无需登录到 Office 365。 你可以通过任何 Office 365 业务计划获取 SharePoint Online 库和团队网站。 [了解如何将 Office 365 与你的服务器集成](Manage-Office-365-in-Windows-Server-Essentials.md)

 作为奖金，你的用户将能够使用 My Server 2012 R2 应用从任何位置使用其移动设备或 Windows phone 访问 SharePoint Online 库中的文件。 [在哪里可以获得 My Server 应用？](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)

 尚未尝试使用 SharePoint？ [现在可以执行的操作](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)

## <a name="where-on-the-dashboard-will-i-manage-my-libraries-and-team-sites"></a>将在仪表板的哪个位置管理我的库和团队网站？
 将 Office 365 与服务器集成时，你将使用新的 " **SharePoint Online** " 选项卡，该选项卡将添加到仪表板的 "**存储**" 区域中，用于管理 SharePoint Online 资源。


## <a name="what-can-i-manage-from-the-dashboard"></a>可以从仪表板管理哪些内容？

### <a name="manage-your-online-libraries"></a>管理联机的库

- **添加库。** 在“SharePoint 库”**** 选项卡上，使用“添加库”****。 你将能够进行所有常用选择：
  - 选择团队网站和库类型。
  - 确定是否使用版本控制。
  - 分配访问权限。
     **提示：** 若要找出你的库将继承的团队网站权限，请使用**查看站点权限**。
- **打开库。** 若要使用库的内容，需要在 Office 365 中将其打开。 只需选择库并单击“打开库”****。 您可以对内容执行的操作取决于登录到 SharePoint Online 时所用的凭据。
- **更改版本控制或访问权限。** 可以使用“查看库属性”**** 来查看或更改针对库的版本控制或访问权限。
- **删除库。** 在检查以确认库中未存储你以后将需要的任何内容之后，选择该库，然后单击“删除库”****。 **警告：** 删除 SharePoint Online 库之前，请确保保存任何要保留到其他位置的文件。 从 SharePoint 中删除库时，所有内容都将被永久删除。 无法检索任何内容。

### <a name="manage-your-team-sites"></a>管理团队网站

- **管理 SharePoint 团队站点。** "**管理团队网站**" 操作允许你登录到 Office 365 并管理你的 SharePoint Online 团队网站。 你可以在 Office 365 中执行的操作将由你用来登录的联机帐户确定。 关闭 Office 365 并返回到仪表板时，单击 "**刷新**" 以显示所做的更改。
- **查看或更改团队网站权限。** 由于库默认从其团队网站继承权限，因此很有必要轻松访问团队网站。 若要查看或更改团队网站的权限，请选择该团队网站或它的任何库，然后单击 **"查看网站权限"**。 **提示：** 需要有关 SharePoint 团队网站权限的精细点的帮助吗？ “团队网站权限”中有一个实用的 [了解详细信息](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924) 链接。

## <a name="tips"></a>提示

-   **单击 "刷新" 以显示 Office 365 门户中进行的最新更改。** 打开 Office 365 以管理 SharePoint Online 后，您将需要刷新显示。 如果使仪表板长期保持打开状态，则请单击“刷新”**** 以确保你看到的是最新更改。

-   **可在 SharePoint Online 中执行的操作取决于你使用的是仪表板还是 Office 365。** 在仪表板上，SharePoint Online 更改使用 Office 365 集成的管理员帐户进行。 但是，当你从仪表板登录到 Office 365 时，你所使用的联机帐户的访问权限将决定你可以执行的操作。

     若要找出 Office 365 集成的管理员帐户，请在仪表板上打开 " **office 365** " 选项卡。

## <a name="other-things-you-might-want-to-do"></a>你可能希望执行的其他操作

-   [通过 My Server 应用从任意位置使用 SharePoint Online 库](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)

-   [了解有关为 SharePoint 团队网站分配权限的详细信息](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924)

-   [了解可以使用 SharePoint 功能执行的操作](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)

-   [了解可用的 Office 365 企业版计划](https://office.microsoft.com/business/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&WT.srch=1&WT.mc_ID=PS_bing_O365Comm_what-is-office-365-for_Text)

-   [将 Office 365 与服务器集成](Manage-Office-365-in-Windows-Server-Essentials.md)

-   [从仪表板管理其他 Microsoft Online Services](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)
