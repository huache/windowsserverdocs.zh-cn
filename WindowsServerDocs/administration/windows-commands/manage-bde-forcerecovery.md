---
title: manage-bde forcerecovery
description: Manage-bde forcerecovery 命令的参考文章，用于在重新启动时强制 BitLocker 保护的驱动器进入恢复模式。
ms.topic: reference
ms.assetid: eecae37c-c9a3-46c5-b615-a0ace1f1d778
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b88aa4bb52ea6bcb50f34a6e8d42c6e14e0b1e59
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622618"
---
# <a name="manage-bde-forcerecovery"></a>manage-bde forcerecovery

重新启动时，强制 BitLocker 保护的驱动器进入恢复模式。 此命令从驱动器中删除所有受信任的平台模块 (与 TPM) 相关的密钥保护程序。 计算机重新启动时，只能使用恢复密码或恢复密钥来解锁驱动器。

## <a name="syntax"></a>语法

```
manage-bde –forcerecovery <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
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

若要使 BitLocker 在驱动器 C 上以恢复模式启动，请键入：

```
manage-bde –forcerecovery C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
