---
title: auditpol
description: 用于显示有关和执行函数来操作审核策略的 auditpol 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a02cfb9d-732f-4e77-aeba-f18265daa3af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89fee7ccd3b6671a6f2633c3b5d15d0cbee261fa
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718837"
---
# <a name="auditpol"></a>auditpol

显示有关和执行操作审核策略的功能的信息，包括：

- 设置和查询系统审核策略。

- 设置和查询每个用户的审核策略。

- 设置和查询审核选项。

- 设置和查询用于委托审核策略访问的安全描述符。

- 向逗号分隔值（CSV）文本文件报告或备份审核策略。

- 从 CSV 文本文件加载审核策略。

- 配置全局资源 Sacl。

## <a name="syntax"></a>语法

```
auditpol command [<sub-command><options>]
```

### <a name="parameters"></a>参数

| 子命令 | 描述 |
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

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
