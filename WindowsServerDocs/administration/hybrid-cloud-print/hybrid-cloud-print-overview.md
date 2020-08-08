---
title: Windows Server 混合云打印概述
description: 混合云打印允许 IT 专业人员支持 BYOD 或加入域的设备的打印要求。
ms.topic: conceptual
author: trudyha
ms.author: trudyha
ms.date: 10/16/2017
ms.openlocfilehash: 49c5ee234a6983902e7eb2f68e64a058167a3182
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87993417"
---
# <a name="windows-server-hybrid-cloud-print-overview"></a>Windows Server 混合云打印概述

**适用于**
-   Windows Server 2016

## <a name="what-is-hybrid-cloud-print"></a>什么是混合云打印？
**混合云打印**是 Windows Server 2016 的一项新功能，可通过**按需功能**获得。 它允许 IT 专业人员支持自带设备的人员的打印要求，或使用已加入到 Azure Active Directory 的设备。 这包括移动设备，例如 Windows phone、便携式计算机或运行 Windows 10 或 Windows Mobile 的平板电脑。 它提供从任何人都可以访问 Internet 的打印支持。

对于 IT 管理员来说，**混合云打印**通过使用 Azure 的多重身份验证来验证用户访问，为本地打印机提供安全的用户访问。 单一登录 (SSO) 功能可简化用户体验。 **混合云打印**在 Windows**打印服务器**角色之上，为 IT 专业人员提供类似于管理打印机和用户访问安全性的体验。

通过**混合云打印**，你的组织中的用户可以从他们用于完成其工作的设备进行打印，即使他们离开办公桌或工作区。

Windows 10 创意者更新和 Windows 10 S 中支持**混合云打印**。

## <a name="feature-summary"></a>功能摘要
**混合云打印**包括两个主服务器端组件：**发现**服务和**Windows 打印**服务。
- 在 IIS 服务上运行的**发现**服务终结点，支持在云中使用 Mopria 同盟工业标准来进行打印机发现。
- **Windows 打印**服务终结点在支持行业标准 Internet 打印协议 (IPP) 的 IIS 服务上运行，以确保最广泛的客户端操作系统支持。

## <a name="deployment"></a>部署
**混合云打印**支持多种不同的部署选项，具体取决于你的组织需要进行用户身份验证的位置。 部署如下所示：

![显示混合云打印解决方案的图形描述的关系图](../media/hybrid-cloud-print/wshcp-deployment-options.png)

*混合云打印解决方案关系图*

该图显示：
- 使用 Azure Active Directory 作为用户标识提供者的**混合云打印**。
- **Windows 打印**服务和**发现**服务终结点已注册到 Azure Active Directory，以使客户端设备能够检索要对这些服务使用的所需用户身份验证令牌。
- MDM 服务（如**Microsoft Intune**）使用将 Azure Active Directory 连接到**Windows 打印**服务和**发现**服务所需的策略来预配客户端设备。

此表包含有关关系图中的元素的详细信息。

| 元素 | 描述 |
| ------- | ----------- |
| Azure Active Directory  | 提供和控制用户标识和授权功能 |
| Active Directory        | 提供和控制用户标识和授权功能 |
| Azure AD Connect  | 同步 Azure AD 和本地 AD 之间的用户凭据。 |
| MDM 服务 (Intune)  | 提供设备策略设置功能，以确保客户端设备 (BYOD 设备) 符合公司策略。 |
| Azure AD 代理 | 提供从防火墙后面建立的长期连接，以允许特定的已配置应用程序流量从 Internet 流动到企业网络。 |
| Azure Web 应用 | 混合云打印解决方案的核心。 提供所需的 web 终结点以发现打印机，并为未加入域的设备发送打印内容。 |
| BYOD 设备/Windows 打印服务器后台处理程序/打印机 | 它们按原样进行。 不会更改部署中的功能。 |

可以通过两种方法安装**混合云打印**：
- * * 点播功能，请参阅在[Windows Server 中配置按需功能](../server-manager/configure-features-on-demand-in-windows-server.md)，了解有关添加和删除角色和功能文件的详细信息。
- * * Windows Server 2016 设置，管理员可以在 "**设置**" "  ->  **应用**  ->  " "**管理可选功能**  ->  " 中**添加功能**并搜索功能点播包
- PowerShell 命令-在 PowerShell 管理员窗口中运行以下命令：

```PowerShell
    Install-Module -Name PublishCloudPrinter
    Import-Module PublishCloudPrinter
```