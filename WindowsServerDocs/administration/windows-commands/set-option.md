---
title: Set 选项
description: Set 选项的参考文章，用于设置创建卷影副本的选项。
ms.topic: article
ms.assetid: 4d8d4921-9fdd-4a3c-bb0f-9df5458c4b84
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 148efa02509678de65af7b2555094fbcb2a3fb55
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87882607"
---
# <a name="set-option"></a>Set 选项

设置创建卷影副本的选项。 如果不使用参数， **set 选项将**在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

### <a name="parameters"></a>参数

|     参数     |                                                                                                  描述                                                                                                  |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   [差异   |                                                                                                     丛                                                                                                     |
|  便携  |                       指定还不导入卷影副本。 稍后可以使用元数据 .cab 文件将卷影副本导入到相同或不同的计算机。                       |
| [rollbackrecover] |                     向编写器发出在**PostSnapshot**事件期间使用*自动恢复*的信号。 如果卷影副本将用于 rollback (例如，使用数据挖掘) ，则此方法很有用。                      |
|   [txfrecover]    |                                                               请求 VSS 使卷影副本在创建过程中处于事务一致状态。                                                                |
|  [noautorecover]  | 使写入程序和文件系统不会将卷影副本的任何恢复更改执行到事务一致状态。 **Noautorecover**不能与**txfrecover**或**rollbackrecover**一起使用。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)