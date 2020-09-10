---
title: manage-bde changepassword
description: 适用于 manage-bde changepassword 命令的参考文章，用于修改数据驱动器的密码。
ms.topic: reference
ms.assetid: b174e152-8442-4fba-8b33-56a81ff4f547
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8c262b6ca123d76af6ebdca09e5546f41350686d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622701"
---
# <a name="manage-bde-changepassword"></a>manage-bde changepassword

修改数据驱动器的密码。 系统将提示用户输入新密码。

## <a name="syntax"></a>语法

```
manage-bde -changepassword [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
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

若要更改用于在数据驱动器 D 上解锁 BitLocker 的密码，请键入：

```
manage-bde –changepassword D:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
