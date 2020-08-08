---
ms.assetid: c60227a8-7b44-40f8-b807-a6532851a4a6
title: 添加属性存储
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: e092cab5a1911c2e710e6f3a9677bf9df987609b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87942689"
---
# <a name="add-an-attribute-store"></a>添加属性存储


需要访问 Active Directory 联合身份验证服务 AD FS 保护的资源的用户帐户和计算机帐户 \( \) 存储在属性存储中，如 Active Directory 域服务 \( AD DS \) 。 声明颁发引擎使用属性存储来收集发出声明所必需的数据。 然后，将属性存储中的数据投影为声明。

你可以使用以下过程将属性存储添加到联合身份验证服务。

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

#### <a name="to-add-an-attribute-store"></a>添加属性存储

1.  打开**AD FS 管理**。

2.  在 "**操作**" 下，单击 "**添加属性存储**"。

![添加属性存储](media/Add-an-Attribute-Store/addstore1.PNG)

3. 在 "**添加属性存储**" 对话框中，为要添加的属性存储配置以下属性：

   -   在 "**显示名称**" 中，键入要用于标识属性存储的名称。

   -   在 "**属性存储类型**" 中，选择支持的属性存储类型（ **Active Directory**、 **LDAP**或**SQL**）。

   -   在 "**连接字符串**" 中，如果已选择 "轻型目录访问协议 \( LDAP 存储" 或 " \) 结构化查询语言 \( SQL 存储" \) ，请输入用于建立到属性存储的连接的字符串。 对于 Active Directory 属性存储，无需连接字符串;因此，此字段处于禁用状态。

       > [!NOTE]
       > 默认情况下，AD FS 会自动创建 Active Directory 属性存储。

![添加属性存储](media/Add-an-Attribute-Store/addstore2.PNG)

4. 单击“确定”。

## <a name="additional-references"></a>其他参考

[AD FS 操作](../ad-fs-operations.md)

[属性存储的角色](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md)
