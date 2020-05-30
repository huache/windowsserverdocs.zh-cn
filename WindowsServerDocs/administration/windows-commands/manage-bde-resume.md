---
title: manage-bde 恢复
description: Manage-bde resume 命令的参考主题，它在暂停后恢复 BitLocker 加密或解密。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ca3cd1ca-6f2c-4190-b68f-27816635facb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17a41a0a5c97bb20c1010c968e495ffbc81649cf
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222120"
---
# <a name="manage-bde-resume"></a>manage-bde 恢复

在暂停后恢复 BitLocker 加密或解密。

## <a name="syntax"></a>语法

```
manage-bde -resume [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要在驱动器 C 上恢复 BitLocker 加密，请键入：

```
manage-bde –resume C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde on 命令](manage-bde-on.md)

- [manage-bde off 命令](manage-bde-off.md)

- [manage-bde pause 命令](manage-bde-pause.md)

- [manage-bde 命令](manage-bde.md)
