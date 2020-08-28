---
title: auditpol clear
description: 用于删除所有用户的每用户审核策略、重置 (禁用所有子类别的系统审核策略) 并将所有审核选项设置为已禁用的 auditpol clear 命令的参考文章。
ms.topic: reference
ms.assetid: 05bfa218-2434-4ad1-b33c-e6fcfb2b4f67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ba2a4759d5c1aacdf6fae27e00a9a2e74b4597dc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029105"
---
# <a name="auditpol-clear"></a>auditpol clear

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除所有用户的每用户审核策略，重置 (禁用所有子类别的系统审核策略) ，并将所有审核选项设置为 "禁用"。

若要对*每个用户*和*系统*策略执行*清除*操作，您必须对安全描述符中的该对象集具有 "**写入**" 或 "**完全控制**" 权限。 如果有 "**管理审核和安全日志** (") 用户权限，还可以执行*清除*操作。 但是，此权限允许执行整体 *清除* 操作所不需要的其他访问权限。

## <a name="syntax"></a>语法

```
auditpol /clear [/y]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ----------- | --------------- |
| /y | 禁止提示确认是否应清除所有审核策略设置。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要为所有用户删除每用户审核策略，请重置 (禁用) 所有子类别的系统审核策略，并将所有审核策略设置设置为 "已禁用"，并在确认提示符下键入：

```
auditpol /clear
```

若要为所有用户删除每用户审核策略，请重置所有子类别的系统审核策略设置，并将所有审核策略设置设置为 "已禁用"，而无需确认提示，请键入：

```
auditpol /clear /y
```

> [!NOTE]
> 使用脚本执行此操作时，上述示例非常有用。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [auditpol 命令](auditpol.md)
