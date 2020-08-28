---
title: auditpol
description: Auditpol 命令的参考文章，其中显示了有关的信息和执行函数来操作审核策略。
ms.topic: reference
ms.assetid: a02cfb9d-732f-4e77-aeba-f18265daa3af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b4a945d1779c3a55fd6647e366770e7ee3d9ec67
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028955"
---
# <a name="auditpol"></a>auditpol

显示有关和执行操作审核策略的功能的信息，包括：

- 设置和查询系统审核策略。

- 设置和查询每个用户的审核策略。

- 设置和查询审核选项。

- 设置和查询用于委托审核策略访问的安全描述符。

- 以逗号分隔的值报告或备份审核策略 (CSV) 文本文件。

- 从 CSV 文本文件加载审核策略。

- 配置全局资源 Sacl。

## <a name="syntax"></a>语法

```
auditpol command [<sub-command><options>]
```

### <a name="parameters"></a>参数

| 子命令 | 说明 |
| ----------- | ----------- |
| /get | 显示当前审核策略。 有关详细信息，请参阅 [auditpol get](auditpol-get.md) for 语法和 options。 |
| /set | 设置审核策略。 有关详细信息，请参阅适用于语法和选项的 [auditpol 集](auditpol-set.md) 。 |
| /list | 显示可选的策略元素。 有关详细信息，请参阅适用于语法和选项的 [auditpol list](auditpol-list.md) 。 |
| /backup | 将审核策略保存到文件。 有关详细信息，请参阅适用于语法和选项的 [auditpol backup](auditpol-backup.md) 。 |
| /restore | 从以前使用 auditpol/backup. 创建的文件还原审核策略。 有关详细信息，请参阅适用于语法和选项的 [auditpol restore](auditpol-restore.md) 。 |
| /clear | 清除审核策略。 有关详细信息，请参阅适用于语法和选项的 [auditpol clear](auditpol-clear.md) 。 |
| /remove | 删除所有每用户审核策略设置，并禁用所有系统审核策略设置。 有关详细信息，请参阅 [auditpol remove](auditpol-remove.md) for 语法和 options。 |
| /resourceSACL | 配置全局资源系统访问控制列表 (Sacl) 。 **注意：** 仅适用于 Windows 7 和 Windows Server 2008 R2。 有关详细信息，请参阅 [Auditpol resourceSACL](auditpol-resourcesacl.md)。 |
| /?| 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
