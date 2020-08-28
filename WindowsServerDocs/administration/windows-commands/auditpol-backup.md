---
title: auditpol backup
description: 引用用于将系统审核策略设置、所有用户的按用户审核策略设置和所有审核选项设置为逗号分隔值 (CSV) 文本文件的引用项目。
ms.topic: reference
ms.assetid: dc84e581-aa0f-4c91-b13b-1d970bad5517
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4c5dc71ef737c3c939d895a0693ff8213105caa1
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029145"
---
# <a name="auditpol-backup"></a>auditpol backup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将所有用户的系统审核策略设置、每用户审核策略设置和所有审核选项 (CSV) 文本文件备份为逗号分隔值。

若要对*每个用户*和*系统*策略执行*备份*操作，您必须对安全描述符中的该对象集具有 "**写入**" 或 "**完全控制**" 权限。 如果你具有 "**管理审核和安全日志** (") 用户权限，则还可以执行*备份*操作。 但是，此权限允许执行整个 *备份* 操作所不需要的其他访问权限。

## <a name="syntax"></a>语法

```
auditpol /backup /file:<filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|-----------|------------- |
| /file | 指定审核策略将备份到的文件的名称。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要将所有用户、系统审核策略设置和所有审核选项的每用户审核策略设置备份到名为 auditpolicy.csv 的 CSV 格式的文本文件中，请键入：

```
auditpol /backup /file:C:\auditpolicy.csv
```

> [!NOTE]
> 如果未指定驱动器，则使用当前目录。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [auditpol restore](auditpol-restore.md)

- [auditpol 命令](auditpol.md)
