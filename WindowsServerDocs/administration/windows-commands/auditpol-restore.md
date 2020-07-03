---
title: auditpol restore
description: 用于在语法上与/backup 选项使用的逗号分隔值（CSV）文件格式一致的文件中还原系统审核策略设置、每用户审核策略设置和所有审核选项的引用文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ad73e520-484f-4cf1-a7f9-ae7488e9edf6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7cd9f26189e9237910cfcbe5399c490ddf0c3c0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923673"
---
# <a name="auditpol-restore"></a>auditpol restore

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为所有用户还原系统审核策略设置、每用户审核策略设置，以及从语法上与/backup 选项使用的逗号分隔值（CSV）文件格式一致的文件中的所有审核选项。

若要对*每个用户*和*系统*策略执行*还原*操作，您必须对安全描述符中的该对象集具有 "**写入**" 或 "**完全控制**" 权限。 如果具有 "**管理审核和安全日志**（SeSecurityPrivilege）" 用户权限，则还可以执行*还原*操作，这在发生错误或恶意攻击时还原安全描述符时非常有用。

## <a name="syntax"></a>语法

```
auditpol /restore /file:<filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| /file | 指定应将审核策略还原到的文件。 该文件必须使用/backup 选项创建，或者必须在语法上与/backup 选项使用的 CSV 文件格式一致。 |
| /? |在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要从使用/backup 命令创建的名为 auditpolicy.csv 的文件中还原系统审核策略设置、所有用户的每用户审核策略设置以及所有审核选项，请键入：

```
auditpol /restore /file:c:\auditpolicy.csv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [auditpol backup](auditpol-backup.md)

- [auditpol 命令](auditpol.md)
