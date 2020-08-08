---
title: 配置 Azure 集成
description: 配置 Azure 集成 Windows 管理中心 (Project Honolulu) 。 将 Windows 管理中心网关连接到 Azure。
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 09/19/2018
ms.localizationpriority: medium
ms.openlocfilehash: c0a19e9bf00667e142c3aa6585c26b69c63e2aa7
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87997347"
---
# <a name="configuring-azure-integration"></a>配置 Azure 集成

>适用于：Windows Admin Center、Windows Admin Center 预览版

Windows 管理中心支持与 Azure 服务集成的多项可选功能。 [了解 Windows 管理中心提供的 Azure 集成选项。](./index.md)

若要允许 Windows 管理中心网关与 Azure 进行通信以利用 Azure Active Directory 的身份验证来进行网关访问，或代表你创建 Azure 资源 (例如，若要使用 Azure Site Recovery) 保护 Windows 管理中心中管理的 Vm，则需要首先向 Azure 注册 Windows 管理中心网关。 你只需为 Windows 管理中心网关执行此操作一次，将网关更新到较新版本时，会保留此设置。

## <a name="register-your-gateway-with-azure"></a>向 Azure 注册你的网关

首次尝试使用 Windows 管理中心中的 Azure 集成功能时，系统将提示你将网关注册到 Azure。 你还可以通过转到 Windows 管理中心 "设置" 中的 " **Azure** " 选项卡来注册网关。 请注意，只有 Windows 管理中心网关管理员可以向 Azure 注册 Windows 管理中心网关。 [了解有关 Windows 管理中心用户和管理员权限的详细信息](../configure/user-access-control.md#gateway-access-role-definitions)。

指导式产品内步骤会在你的目录中创建一个 Azure AD 应用，以便 Windows 管理中心能够与 Azure 通信。 若要查看自动创建的 Azure AD 应用，请参阅 Windows 管理中心设置的**Azure**选项卡。 " **Azure** " 超链接中的视图可让你查看 Azure 门户中的 Azure AD 应用。

创建的 Azure AD 应用用于 Windows 管理中心中的所有 Azure 集成点，包括[网关 Azure AD 身份验证](../configure/user-access-control.md#azure-active-directory)。 Windows 管理中心自动配置代表您创建和管理 Azure 资源所需的权限：

- Azure Active Directory Graph
    - Directory.AccessAsUser.All
    - User.Read
- Azure 服务管理
    - user_impersonation

### <a name="manual-azure-ad-app-configuration"></a>手动 Azure AD 应用配置

如果要手动配置 Azure AD 应用，而不是在网关注册过程中使用 Windows 管理中心自动创建的 Azure AD 应用，则必须执行以下操作。

1. 将上面列出的所需 API 权限授予 Azure AD 应用。 可以通过导航到 Azure 门户中的 Azure AD 应用来完成此操作。 请参阅 Azure 门户 > **Azure Active Directory**"  >  **应用注册**" > 选择要使用的 Azure AD 应用。 然后添加到 " **api 权限**" 选项卡，并添加上面列出的 api 权限。
2. 将 Windows 管理中心网关 URL 添加到回复 Url (也称为重定向 Uri) 。 导航到 Azure AD 应用，然后转到 "**清单**"。 在清单中查找 "replyUrlsWithType" 键。 在注册表项中，添加包含两个键的对象： "url" 和 "type"。 密钥 "url" 的值应为 Windows 管理中心网关 URL，并在末尾追加通配符。 键 "type" 键的值应为 "Web"。 例如：

    ```json
    "replyUrlsWithType": [
            {
                    "url": "http://localhost:6516/*",
                    "type": "Web"
            }
    ],
    ```