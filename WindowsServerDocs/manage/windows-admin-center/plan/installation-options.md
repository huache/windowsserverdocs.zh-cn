---
title: 哪种安装类型适合你
description: 本主题介绍 Windows Admin Center 的不同安装选项，包括在 Windows 10 电脑或 Windows 服务器上安装以供多个管理员使用。
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 12/02/2019
ms.openlocfilehash: 503cd64cac0673829fe21bc15e8ad9d6a83bbb15
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950518"
---
# <a name="what-type-of-installation-is-right-for-you"></a>哪种安装类型适合你？

本主题介绍 Windows Admin Center 的不同安装选项，包括在 Windows 10 电脑或 Windows 服务器上安装以供多个管理员使用。 若要在 Azure 中的 VM 上安装 Windows Admin Center，请参阅[在 Azure 中部署 Windows Admin Center](../azure/deploy-wac-in-azure.md)。

## <a name="installation-types"></a>安装：类型

![img](../media/deployment-options/install-options.PNG)

| 本地客户端                                | 网关服务器                                  | 托管服务器                               | 故障转移群集                           |
|---------------------------------------------|-------------------------------------------------|----------------------------------------------|--------------------------------------------|
| 在连接到托管服务器的本地 Windows 10 客户端上[安装](../deploy/install.md)。  适用于快速入门、测试、即席或小规模方案。 |在指定的网关服务器上[安装](../deploy/install.md)，并从连接到网关服务器的任何客户端浏览器进行访问。  适用于大规模方案。 | 直接在托管服务器上[安装](../deploy/install.md)，以管理自身或其成员节点所在的群集。  适用于分布式方案。 | 在故障转移群集中[部署](#high-availability)以实现网关服务的高可用性。 适用于生产环境，以确保管理服务的复原能力。 |

## <a name="installation-supported-operating-systems"></a>安装：支持的操作系统

你可以在以下 Windows 操作系统上安装 Windows Admin Center  ：

| **平台**                       | **安装模式** |
| -----------------------------------| --------------------- |
| Windows 10                         | 本地客户端 |
| Windows Server 半年频道 | 网关服务器、托管服务器、故障转移群集 |
| Windows Server 2016                | 网关服务器、托管服务器、故障转移群集 |
| Windows Server Standard 2012 R2                | 网关服务器、托管服务器、故障转移群集 |

若要操作 Windows Admin Center：

- **在本地客户端方案中：** 从“开始”菜单启动 Windows Admin Center 网关，并通过访问 `https://localhost:6516` 从客户端 Web 浏览器连接到该网关。
- **在其他方案中：** 通过 URL（如 `https://servername.contoso.com`）从客户端浏览器连接到不同计算机上的 Windows Admin Center 网关

> [!WARNING]
> 不支持在域控制器上安装 Windows Admin Center。 [详细了解域控制器安全最佳做法](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/securing-domain-controllers-against-attack)。

## <a name="installation-supported-web-browsers"></a>安装：支持的 Web 浏览器

Microsoft Edge（包括 [Microsoft Edge insider](https://microsoftedgeinsider.com)）和 Google Chrome 在 Windows 10 上经过测试并获得支持。 其他 Web 浏览器（包括 Internet Explorer 和 Firefox）当前不在我们的测试矩阵中，因此不受正式支持  。 这些浏览器在运行 Windows Admin Center 时可能会遇到问题。 例如，Firefox 有自己的证书存储，因此你必须将 `Windows Admin Center Client` 证书导入到 Firefox 中才能在 Windows 10 上使用 Windows Admin Center。 有关更多详细信息，请参阅[特定于浏览器的已知问题](../support/known-issues.md#browser-specific-issues)。

## <a name="management-target-supported-operating-systems"></a>管理目标：支持的操作系统

你可以使用 Windows Admin Center 管理以下 Windows 操作系统  ：

| 版本 | 通过服务器管理器管理节点   | 通过群集管理器进行管理  |
| ------------------------- |--------------- | ----- |
| Windows 10 | 是（通过计算机管理） | N/A |
| Windows Server 半年频道 | 是 | 是 |
| Windows Server Standard 2012 R2 | 是 | 是 |
| Windows Server 2016 | 是 | 是，具有[最新累积更新](../use/manage-hyper-converged.md#prepare-your-windows-server-2016-cluster-for-windows-admin-center) |
| Microsoft Hyper-V Server 2016 | 是 | 是 |
| Windows Server 2012 R2 | 是 | 是 |
| Microsoft Hyper-V Server 2012 R2 | 是 | 是 |
| Windows Server 2012 | 是 | 是 |
| Windows Server 2008 R2 | 是，功能有限 | N/A |

> [!NOTE]
> Windows Server 2008 R2、2012 和 2012 R2 中未包含 Windows Admin Center 需要的 PowerShell 功能。 如果你要使用 Windows Admin Center 进行管理，则将需要在这些服务器上安装 Windows Management Framework (WMF) 5.1 或更高版本。
> 
> 在 PowerShell 中键入 `$PSVersiontable`，以验证是否安装了 WMF 并且版本是否为 5.1 或更高版本。 
> 
> 如果未安装 WMF，可以[下载 WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616)。

## <a name="high-availability"></a>高可用性

可以通过在故障转移群集上的主动-被动模型中部署 Windows Admin Center 来实现网关服务的高可用性。 如果群集中的某个节点发生故障，Windows Admin Center 会正常故障转移到另一个节点，从而使你可以无缝继续管理环境中的服务器。

[了解如何部署具有高可用性的 Windows Admin Center。](../deploy/high-availability.md)

> [!Tip]
> 已准备好安装 Windows Admin Center？ [立即下载](https://aka.ms/windowsadmincenter)
