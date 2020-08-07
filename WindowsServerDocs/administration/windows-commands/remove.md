---
title: remove
description: 删除命令的参考文章，用于从卷中删除驱动器号或装入点。
ms.topic: article
ms.assetid: b0886140-da8b-4231-8cb2-f280874d99c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 469b3ac1783dfff5228778d11532448bee49346c
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883832"
---
# <a name="remove"></a>remove

从选中的卷删除驱动器号或装入点。 如果使用了 all 参数，就会删除所有当前驱动器号和装入点。 如果未指定驱动器号或装入点，则 DiskPart 将删除其遇到的第一个驱动器号或装入点。

"删除" 命令还可用于更改与可移动驱动器关联的驱动器号。 不能删除系统卷、启动卷或分页卷上的驱动器号。 此外，无法删除 OEM 分区、具有无法识别的 GUID 的任何 GPT 分区或任何特殊的非数据分区分区（如 EFI 系统分区）的驱动器号。

> [!NOTE]
> 必须选择一个卷，"**删除**" 命令才会成功。 使用 "[选择卷](select-volume.md)" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
remove [{letter=<drive> | mount=<path> [all]}] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 字母 =`<drive>` | 要删除的驱动器号。 |
| 装载 =`<path>` | 要删除的装入点路径。 |
| all | 删除所有当前的驱动器号和装入点。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

删除 d:\驱动器，请键入：

```
remove letter=d
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
