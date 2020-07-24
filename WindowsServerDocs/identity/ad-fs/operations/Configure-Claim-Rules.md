---
ms.assetid: 9cafa3e1-8118-4a75-a7c2-1dbe40b1a444
title: 配置声明规则
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 62671800d923e95c6bc3f9c7efb0660974c438e2
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954279"
---
# <a name="configure-claim-rules"></a>配置声明规则

在基于声明的 \- 标识模型中，Active Directory 联合身份验证服务 \( AD FS \) 为联合身份验证服务的功能是颁发包含一组声明的令牌。 声明规则管理有关 AD FS 问题的声明的决策。 声明规则和所有服务器配置数据均存储在 AD FS 配置数据库中。  
  
AD FS 根据声明和其他上下文信息的形式向其提供的标识信息进行颁发决策。 从较高层次来看，AD FS 将一组声明作为输入，执行多个转换，然后返回一组不同的声明作为一个规则处理器。 

以下主题将帮助你创建 AD FS 将处理的规则： 
  
-   [创建传递或筛选传入声明的规则](Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [创建规则以允许所有用户](Create-a-Rule-to-Permit-All-Users.md)  
  
-   [创建规则以根据传入声明允许或拒绝用户](Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [创建规则以将 LDAP 属性作为声明发送](Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [创建规则以声明方式发送组成员身份](Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [创建规则以转换传入声明](Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [创建规则以发送身份验证方法声明](Create-a-Rule-to-Send-an-Authentication-Method-Claim.md) 
-   [创建规则以发送 AD FS 1.x 兼容声明](Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md) 
  
-   [创建规则以使用自定义规则发送声明](Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)  

## <a name="see-also"></a>另请参阅  
[AD FS 操作](../ad-fs-operations.md) 
