---
title: 使用 Windows Admin Center 的用户访问选项
description: 使用 Windows Admin Center (Project Honolulu) 的用户访问选项和标识提供者
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 03/07/2019
ms.localizationpriority: medium
ms.openlocfilehash: 3c96968f55a06c7ccffd9f7919001f21bff6a75c
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87996985"
---
# <a name="user-access-options-with-windows-admin-center"></a>使用 Windows Admin Center 的用户访问选项

>适用于：Windows Admin Center、Windows Admin Center 预览版

在 Windows Server 上部署时，Windows Admin Center 为服务器环境提供了集中管理点。 通过控制对 Windows Admin Center 的访问权限，可以提高管理环境的安全性。

## <a name="gateway-access-roles"></a>网关访问权限角色

Windows Admin Center 定义了两个用于访问网关服务的角色：网关用户和网关管理员。

> [!NOTE]
> 可以访问网关并不意味着可以访问对网关可见的目标服务器。 若要管理目标服务器，用户必须使用在目标服务上具有管理权限的凭据进行连接。

**网关用户**可以连接到 Windows Admin Center 网关服务，以便通过该网关管理服务器，但他们不能更改访问权限，也不能更改身份验证机制（用于向网关进行身份验证）。

**网关管理员**可以对谁获得访问权限以及用户如何向网关进行身份验证进行配置。

>[!NOTE]
> 如果 Windows Admin Center 中未定义访问组，则这些角色将反映 Windows 帐户对网关服务器的访问权限。

[在 Windows Admin Center 中配置网关用户和管理员访问权限。](../configure/user-access-control.md)

## <a name="identity-provider-options"></a>标识提供者选项

网关管理员可以选择以下任一项：

 - [Active Directory/本地计算机组](../configure/user-access-control.md#active-directory-or-local-machine-groups)
 - [Azure Active Directory 作为 Windows Admin Center 的标识提供者](../configure/user-access-control.md#azure-active-directory)


### <a name="smartcard-authentication"></a>智能卡身份验证

使用 Active Directory 或本地计算机组作为标识提供者时，可以通过要求访问 Windows Admin Center 的用户成为其他基于智能卡的安全组的成员，来强制执行智能卡身份验证。 [在 Windows Admin Center 中配置智能卡身份验证。](../configure/user-access-control.md#active-directory-or-local-machine-groups)

### <a name="conditional-access-and-multi-factor-authentication"></a>条件访问和多重身份验证

通过要求对网关进行 Azure AD 身份验证，你可以使用 Azure AD 提供的其他安全功能，例如条件访问和多重身份验证。 [详细了解如何使用 Azure Active Directory 配置条件访问。](/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)

## <a name="role-based-access-control"></a>基于角色的访问控制

默认情况下，用户需要使用 Windows Admin Center 对其要管理的计算机拥有完全的本地管理员权限。
可借此远程连接到计算机，并确保拥有足够的权限来查看和修改系统设置。
但是，某些用户可能需要拥有对计算机的有限访问权限才能执行其作业。
你可以在 Windows Admin Center 中使用基于角色的访问控制，为此类用户提供对计算机的有限访问权限，而不是让用户成为具有完全权限的本地管理员  。

Windows Admin Center 中基于角色的访问控制的工作方式是通过使用 PowerShell [Just Enough Administration](https://aka.ms/jeadocs) 终结点配置每个托管服务器。
此终结点定义了角色，包括允许每个角色管理系统的哪些方面以及将哪些用户分配给该角色。
用户连接到受限制的终结点时，将创建一个临时的本地管理员帐户，以通过用户身份管理系统。
这样可以确保即使没有自己的委派模型的工具仍可以使用 Windows Admin Center 进行管理。
用户通过 Windows Admin Center 停止管理计算机时，自动删除临时帐户。

用户连接到配置了基于角色的访问控制的计算机时，Windows Admin Center 将首先检查这些用户是否是本地管理员。
如果用户是本地管理员，他们将获得无限制的完整 Windows Admin Center 体验。
否则，Windows Admin Center 将检查用户是否属于任何预定义的角色。
如果用户属于 Windows Admin Center 角色但不是完全权限管理员，则称该用户具有有限制的访问权限  。
最后，如果用户既不是管理员也不是角色的成员，则将拒绝他们对计算机的管理访问权限。

基于角色的访问控制可用于服务器管理器和故障转移群集解决方案。

### <a name="available-roles"></a>可用角色

Windows Admin Center 支持以下最终用户角色：

角色名称 | 预期用途
----------|-------------
Administrators | 允许用户在没有获得对远程桌面或 PowerShell 的访问权限的情况下使用 Windows Admin Center 中的大部分功能。 此角色适用于想要限制计算机上的管理入口点的“跳转服务器”方案。
Readers | 允许用户查看服务器上的信息和设置，但不允许对其进行更改。
Hyper-V 管理员 | 允许用户更改 Hyper-V 虚拟机和交换机，但将其他功能限制为只读访问权限。

用户使用受限制的访问权限进行连接时，以下内置扩展具有精简功能：

- 文件（无文件上传或下载）
- PowerShell（不可用）
- 远程桌面（不可用）
- 存储副本（不可用）

目前，无法为组织创建自定义角色，但是可以选择授予访问其每个角色的权限的用户。

### <a name="preparing-for-role-based-access-control"></a>准备基于角色的访问控制

若要利用临时本地帐户，需要将每台目标计算机配置为支持 Windows Admin Center 中基于角色的访问控制。
配置过程涉及使用 Desired State Configuration 在计算机上安装 PowerShell 脚本和 Just Enough Administration 终结点。

如果只有几台计算机，则可以使用 Windows Admin Center 中的基于角色的访问控制页轻松地将配置分别应用到每台计算机。
在一台计算机上设置基于角色的访问控制时，将创建本地安全组以控制对每个角色的访问权限。
可以通过将用户或其他安全组添加为角色安全组的成员来授予其访问权限。

对于在多台计算机上进行企业范围的部署，你可以从网关下载配置脚本，然后使用 Desired State Configuration 拉取服务器、Azure 自动化或首选的管理工具将其分发到计算机上。