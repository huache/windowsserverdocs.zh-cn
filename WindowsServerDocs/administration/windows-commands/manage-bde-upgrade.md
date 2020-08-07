---
title: manage-bde 升级
description: Manage-bde 升级命令的参考文章，用于升级 BitLocker 版本。
ms.topic: article
ms.assetid: 23bfa824-6ff0-44cc-9b8b-b199a769fb8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 33f4e243d14465d2bc89b5723a0d92a98489dc59
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886616"
---
# <a name="manage-bde-upgrade"></a>manage-bde 升级

升级 BitLocker 版本。

## <a name="syntax"></a>语法

```
manage-bde -upgrade [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

## <a name="examples"></a>示例

若要在驱动器 C 上升级 BitLocker 加密，请键入：

```
manage-bde –upgrade C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
