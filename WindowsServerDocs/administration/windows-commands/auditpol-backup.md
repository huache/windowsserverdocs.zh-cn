---
title: auditpol 备份
description: 适用于**auditpol 备份**的 Windows 命令主题，该主题备份系统审核策略设置、将所有用户的每个用户审核策略设置和逗号分隔值（CSV）文本文件的所有审核选项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dc84e581-aa0f-4c91-b13b-1d970bad5517
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8895f312606a6a6c45a77c659a1cd98d115babe3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851210"
---
# <a name="auditpol-backup"></a>auditpol 备份

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将所有用户的系统审核策略设置、每用户审核策略设置以及逗号分隔值（CSV）文本文件备份到所有审核选项。

## <a name="syntax"></a>语法

```
auditpol /backup /file:<filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|-----------|------------- |
| /file | 指定审核策略将备份到的文件的名称。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

对于每用户策略和系统策略的备份操作，您必须对安全描述符中的该对象集具有 "写入" 或 "完全控制" 权限。 还可以通过拥有 "**管理审核和安全日志**（SeSecurityPrivilege）" 用户权限来执行备份操作。 但是，此权限允许执行列表操作所不需要的其他访问权限。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将所有用户、系统审核策略设置和所有审核选项的每用户审核策略设置备份到名为 auditpolicy 的 CSV 格式的文本文件中，请键入：

```
auditpol /backup /file:C:\auditpolicy.csv
```

> [!NOTE]
> 如果未指定驱动器，则使用当前目录。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
- [auditpol 还原](auditpol-restore.md)
