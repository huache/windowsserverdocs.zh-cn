---
title: manage-bde setidentifier
description: Manage-bde setidentifier 命令的参考文章，可将驱动器上的驱动器标识符字段设置为在为组织提供唯一标识符组策略设置中指定的值。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7092d18f-4ac9-4c73-a20f-1246ca60e75e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c6a04b4f7c04174158a165cf0d41493078af0056
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957039"
---
# <a name="manage-bde-setidentifier"></a>manage-bde setidentifier

将驱动器上的 "驱动器标识符" 字段设置为 "为**你的组织提供唯一标识符**组策略" 设置中指定的值。

## <a name="syntax"></a>语法

```
manage-bde –setidentifier <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要设置 C 的 BitLocker 驱动器标识符字段，请键入：

```
manage-bde –setidentifier C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)

- [BitLocker 恢复指南](/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)
