---
title: 选择是在自己的新林中还是在现有堡垒林中安装 HGS
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 46dc032527bf918211aa55c5b69c1dcbf4766c86
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971364"
---
# <a name="choose-whether-to-install-hgs-in-its-own-dedicated-forest-or-in-an-existing-bastion-forest"></a>选择是在其自己的专用林中还是在现有堡垒林中安装 HGS

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016


HGS 的 Active Directory 林是敏感的，因为其管理员有权访问控制受防护的 Vm 的密钥。
默认安装将设置一个专用于 HGS 的新林，并配置其他依赖项。
建议使用此选项，因为环境是独立的，并且在创建时被认为是安全的。

在现有林中安装 HGS 的唯一技术要求是添加到根域;非根域不受支持。 但也存在使用现有林的操作要求和与安全相关的最佳实践。
特意构建适当的林来提供一个敏感功能，如[Privileged Access Management 用于 AD DS](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services)或[增强的安全管理环境 (ESAE) 林](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access-reference-material#ESAE_BM)的林。
此类林通常具有以下特征：

- 它们) 不同于构造管理员的管理员 (
- 它们具有较少的登录数
- 它们在本质上并不是通用的

常规用途林（如生产林）不适合由 HGS 使用。
Fabric 林也不合适，因为 HGS 需要与构造管理员隔离。

## <a name="next-step"></a>后续步骤

选择最适合你的环境的安装选项：

- [在其自己的专用林中安装 HGS](guarded-fabric-install-hgs-default.md)
- [在现有堡垒林中安装 HGS](guarded-fabric-install-hgs-in-a-bastion-forest.md)


