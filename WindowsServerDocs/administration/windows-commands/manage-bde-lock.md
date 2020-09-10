---
title: manage-bde 锁
description: Manage-bde lock 命令的参考文章，它会锁定受 BitLocker 保护的驱动器，以防止对其进行访问，除非提供了解锁密钥。
ms.topic: reference
ms.assetid: b8858e61-3a7e-4d03-8c98-5c09853f35e8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e9b8dfdac7bc8b833a89c9ba447b99984a923f86
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633746"
---
# <a name="manage-bde-lock"></a>manage-bde 锁

锁定受 BitLocker 保护的驱动器，以防止对其进行访问，除非提供了解锁密钥。

## <a name="syntax"></a>语法

```
manage-bde -lock [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要锁定数据驱动器 D，请键入：

```
manage-bde –lock D:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
