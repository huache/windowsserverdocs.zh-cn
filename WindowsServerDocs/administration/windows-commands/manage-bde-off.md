---
title: manage-bde off
description: Manage-bde off 命令的参考文章，用于对驱动器进行解密并关闭 BitLocker。
ms.topic: reference
ms.assetid: 0a27c119-d385-45e5-89fe-e311d4429876
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c85fec912802c6f0bac7494c9a3192623ac55686
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037655"
---
# <a name="manage-bde-off"></a>manage-bde off

解密驱动器并关闭 BitLocker。 解密完成后，将删除所有密钥保护程序。

## <a name="syntax"></a>语法

```
manage-bde -off [<volume>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<volume>` | 指定驱动器号后跟冒号、卷 GUID 路径或装入的卷。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要在驱动器 C 上关闭 BitLocker，请键入：

```
manage-bde –off C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde on 命令](manage-bde-on.md)

- [manage-bde pause 命令](manage-bde-pause.md)

- [manage-bde resume 命令](manage-bde-resume.md)

- [manage-bde 命令](manage-bde.md)
