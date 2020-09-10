---
title: manage-bde autounlock
description: Manage-bde autounlock 命令的参考文章，用于管理受 BitLocker 保护的数据驱动器的自动解锁。
ms.topic: reference
ms.assetid: 063528bf-d235-4b44-887a-52a7d983e01a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e6035b9d4a851631770b01ba525759d1d61992f5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633757"
---
# <a name="manage-bde-autounlock"></a>manage-bde autounlock

管理受 BitLocker 保护的数据驱动器的自动解锁。

## <a name="syntax"></a>语法

```
manage-bde -autounlock [{-enable|-disable|-clearallkeys}] <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -enable | 启用数据驱动器自动解锁。 |
| -disable | 禁用数据驱动器自动解锁。 |
| -clearallkeys | 删除操作系统驱动器上的所有存储的外部密钥。 |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

## <a name="examples"></a>示例

若要对数据驱动器 E 启用自动解锁，请键入：

```
manage-bde –autounlock -enable E:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)