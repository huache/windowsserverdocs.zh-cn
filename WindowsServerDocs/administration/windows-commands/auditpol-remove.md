---
title: auditpol remove
description: 用于删除指定帐户或所有帐户的每用户审核策略的 auditpol remove 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be42ec55-235c-44f7-9abd-ed1cf3f5b1f5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9aedde39d44c7640e6aa2516465e1c8ec7d022c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719091"
---
# <a name="auditpol-remove"></a>auditpol remove

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为指定帐户或所有帐户删除每用户审核策略。

若要对*每个用户*策略执行*删除*操作，你必须对安全描述符中的该对象集具有 "**写入**" 或 "**完全控制**" 权限。 如果有 "**管理审核和安全日志**（SeSecurityPrivilege）" 用户权限，还可以执行*删除*操作。 但是，此权限允许执行整体*删除*操作所不需要的其他访问权限。

## <a name="syntax"></a>语法

```
auditpol /remove [/user[:<username>|<{SID}>]]
[/allusers]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ------- | -------- |
| /user | 指定要为其删除每用户审核策略的用户的安全标识符（SID）或用户名。 |
| /allusers | 删除所有用户的每用户审核策略。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要按名称删除用户 mikedan 的每用户审核策略，请键入：

```
auditpol /remove /user:mikedan
```

若要按 SID 删除用户 mikedan 的每用户审核策略，请键入：

```
auditpol /remove /user:{S-1-5-21-397123471-12346959}
```

若要为所有用户删除每用户审核策略，请键入：

```
auditpol /remove /allusers
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [auditpol 命令](auditpol.md)
