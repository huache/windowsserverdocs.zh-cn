---
title: manage-bde wipefreespace
description: Manage-bde wipefreespace 命令的参考文章，可擦除卷上的可用空间，删除空间中可能存在的任何数据碎片。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b8d83a2a-c5c8-4019-9041-23d1d6abf282
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 872c3722028af1612fb80e3b98650ee0a39261ce
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922177"
---
# <a name="manage-bde-wipefreespace"></a>manage-bde wipefreespace

擦除卷上的可用空间，删除空间中可能存在的任何数据碎片。 使用 "**仅限已用空间**" 加密方法在加密卷上运行此命令时，会提供与 "**整卷加密**" 加密方法相同的保护级别。

## <a name="syntax"></a>语法

```
manage-bde -wipefreespace|-w [<drive>] [-cancel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -cancel | 取消正在进行的擦除可用空间。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要擦除驱动器 C 上的可用空间，请键入： \

```
manage-bde -w C:
```

```
manage-bde -wipefreespace C:
```

若要取消擦除驱动器 C 上的可用空间，请键入：

```
manage-bde -w -cancel C:
```

```
manage-bde -wipefreespace -cancel C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
