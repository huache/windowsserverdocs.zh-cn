---
title: manage-bde changepin
description: Manage-bde changepin 命令的参考文章，用于修改操作系统驱动器的 PIN。
ms.topic: reference
ms.assetid: c85aa1c7-3485-4839-a292-99dfcd6db252
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7b920e9c4580fced678e9d7dddd30fff66dad802
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622634"
---
# <a name="manage-bde-changepin"></a>manage-bde changepin

修改操作系统驱动器的 PIN。 系统将提示用户输入新 PIN。

## <a name="syntax"></a>语法

```
manage-bde -changepin [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
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

若要更改用于驱动器 C 上的 BitLocker 的 PIN，请键入：

```
manage-bde –changepin C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
