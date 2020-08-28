---
title: manage-bde 状态
description: Manage-bde 状态命令的参考文章，其中提供了有关计算机上所有驱动器的信息，而不考虑它们是否受 BitLocker 保护。
ms.topic: reference
ms.assetid: 1444a360-fabf-4dd3-b67f-188e6ea3fa5b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 632e286b15d65c066a6f2229b98e12a23014f998
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027475"
---
# <a name="manage-bde-status"></a>manage-bde 状态

提供有关计算机上所有驱动器的信息;是否受 BitLocker 保护，包括：

- 大小

- BitLocker 版本

- 转换状态

- 加密百分比

- 加密方法

- 保护状态

- 锁定状态

- 标识字段

- 密钥保护程序

## <a name="syntax"></a>语法

```
manage-bde -status [<drive>] [-protectionaserrorlevel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -protectionaserrorlevel | 使 manage-bde 命令行工具发送返回代码 **0** （如果卷受保护）和 **1** （如果卷未受保护）;最常见的批处理脚本用于确定驱动器是否受 BitLocker 保护。 你还可以使用 **-p** 作为此命令的缩写形式。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要显示驱动器 C 的状态，请键入：

```
manage-bde –status C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
