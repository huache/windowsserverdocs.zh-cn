---
ms.assetid: c60227a8-7b44-40f8-b807-a6532851a4a6
title: 添加属性存储
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b197268de3c5335e30c2a24a74c5a7b01224b500
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859690"
---
# <a name="add-an-attribute-store"></a>添加属性存储


需要访问受 Active Directory 联合身份验证服务 \(AD FS\) 保护的资源的用户帐户和计算机帐户将存储在属性存储中，例如 Active Directory 域服务 \(AD DS\)。 声明颁发引擎使用属性存储来收集发出声明所必需的数据。 然后，将属性存储中的数据投影为声明。  
  
你可以使用以下过程将属性存储添加到联合身份验证服务。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   
  
#### <a name="to-add-an-attribute-store"></a>添加属性存储  
  
1.  打开**AD FS 管理**。  
  
2.  在 "**操作**" 下，单击 "**添加属性存储**"。  

![添加属性存储](media/Add-an-Attribute-Store/addstore1.PNG)
  
3. 在 "**添加属性存储**" 对话框中，为要添加的属性存储配置以下属性：  
  
   -   在 "**显示名称**" 中，键入要用于标识属性存储的名称。  
  
   -   在 "**属性存储类型**" 中，选择支持的属性存储类型（ **Active Directory**、 **LDAP**或**SQL**）。  
  
   -   在 "**连接字符串**" 中，如果已选择 "轻型目录访问协议 \(LDAP\) 存储或结构化查询语言 \(SQL\) 存储"，请输入用于建立到属性存储的连接的字符串。 对于 Active Directory 属性存储，无需连接字符串;因此，此字段处于禁用状态。  
  
       > [!NOTE]  
       > 默认情况下，AD FS 会自动创建 Active Directory 属性存储。  
 
![添加属性存储](media/Add-an-Attribute-Store/addstore2.PNG) 

4. 单击“确定”。  
  
## <a name="additional-references"></a>其他参考  

[AD FS 操作](../../ad-fs/AD-FS-2016-Operations.md)
  
[属性存储的角色](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md)  
