---
title: auditpol
description: 适用于**auditpol**的 Windows 命令主题，其中显示了有关的信息和执行函数来操作审核策略。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a02cfb9d-732f-4e77-aeba-f18265daa3af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 00365b0e46b8bff761cf991dbdbd09d8f5e9c687
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851130"
---
# <a name="auditpol"></a>auditpol

显示有关的信息和执行函数以操作审核策略。

有关如何使用此命令的示例，请参阅每个主题中的 "示例" 部分。

## <a name="syntax"></a>语法

```
auditpol command [<sub-command><options>]
```

#### <a name="parameters"></a>参数

| 子命令 | 说明 |
| ----------- | ----------- |
| /get | 显示当前审核策略。 有关详细信息，请参阅[auditpol get](auditpol-get.md) for 语法和 options。 |
| /set | 设置审核策略。 有关详细信息，请参阅适用于语法和选项的[auditpol 集](auditpol-set.md)。 |
| /list | 显示可选的策略元素。 有关详细信息，请参阅适用于语法和选项的[auditpol list](auditpol-list.md) 。 |
| /backup | 将审核策略保存到文件。 有关详细信息，请参阅适用于语法和选项的[auditpol backup](auditpol-backup.md) 。 |
| /restore | 从以前使用 auditpol/backup. 创建的文件还原审核策略。 有关详细信息，请参阅适用于语法和选项的[auditpol restore](auditpol-restore.md) 。 |
| /clear | 清除审核策略。 有关详细信息，请参阅适用于语法和选项的[auditpol clear](auditpol-clear.md) 。 |
| /remove | 删除所有每用户审核策略设置，并禁用所有系统审核策略设置。 有关详细信息，请参阅[auditpol remove](auditpol-remove.md) for 语法和 options。 |
| /resourceSACL | 配置全局资源系统访问控制列表（Sacl）。 **注意：** 仅适用于 Windows 7 和 Windows Server 2008 R2。 有关详细信息，请参阅[Auditpol resourceSACL](auditpol-resourcesacl.md)。 |
| /?| 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

审核策略命令行工具可用于：

- 设置和查询系统审核策略。

- 设置和查询每用户审核策略。

- 设置和查询审核选项。

- 设置和查询用于委托审核策略访问的安全描述符。

- 向逗号分隔值（CSV）文本文件报告或备份审核策略。

- 从 CSV 文本文件加载审核策略。

- 配置全局资源 Sacl。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)