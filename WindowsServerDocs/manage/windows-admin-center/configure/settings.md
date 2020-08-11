---
title: Settings
description: 了解 Windows Admin Center (Project Honolulu) 中的设置。 用户可以使用“用户设置”来更改其语言/区域和其他首选项。 管理员可以使用“网关设置”来配置网关。
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 04/12/2018
ms.localizationpriority: medium
ms.openlocfilehash: ff06a19d85858b8332412a51c029c9aeeba2af50
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87997441"
---
# <a name="windows-admin-center-settings"></a>Windows Admin Center 设置

> 适用于：Windows Admin Center

Windows Admin Center 设置由用户级设置和网关级设置组成。 对用户级设置的更改只会影响当前用户的配置文件，而对网关级设置的更改会影响该 Windows Admin Center 网关上的所有用户。

## <a name="user-settings"></a>用户设置

用户级设置由以下部分构成：

- 帐户
- 个性化设置
- 语言/区域
- 建议
- 高级

在“帐户”  选项卡中，用户可以查看他们用于向 Windows Admin Center 进行身份验证的凭据。 如果将 Azure AD 配置为标识提供程序，用户就可以从此选项卡中注销其 Azure AD 帐户。

在“个性化”  选项卡中，用户可以切换到深色 UI 主题。

在“语言/区域”  选项卡中，用户可以更改 Windows Admin Center 显示的语言和区域格式。

在“建议”  选项卡中，用户可以切换有关 Azure 服务和新功能的建议。

“高级”  选项卡为 Windows Admin Center 扩展开发人员提供附加功能。

## <a name="gateway-settings"></a>网关设置

网关级设置由以下部分构成：

- Extensions
- 访问
- Azure
- 共享连接

只有网关管理员才能查看和更改这些设置。 对这些设置的更改将更改网关的配置，并影响 Windows Admin Center 网关的所有用户。

在“扩展”  选项卡中，管理员可以安装、卸载或更新网关扩展。 [详细了解扩展。](using-extensions.md)

使用“访问”  选项卡，管理员可以配置谁有权访问 Windows Admin Center 网关，以及使用哪个标识提供程序验证用户身份。 [详细了解如何控制对网关的访问。](user-access-control.md)

使用“Azure”  选项卡，管理员可以向 Azure 注册网关，以便在 Windows Admin Center 中启用 [Azure 集成功能](../azure/azure-integration.md)。

使用“共享连接”  选项卡，管理员可以配置要在 Windows Admin Center 网关的所有用户之间共享的单个连接列表。 [详细了解如何一次为网关的所有用户都配置连接。](shared-connections.md)