---
title: 让
description: 公开命令的参考主题，它将持久卷影副本公开为驱动器号、共享或装入点。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d4e8ebf71f6ddcb457460f8174793586e81c73a6
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437172"
---
# <a name="expose"></a>让

将永久性卷影副本作为驱动器号、共享或装入点公开。

## <a name="syntax"></a>语法

```
expose <shadowID> {<drive:> | <share> | <mountpoint>}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| shadowID | 指定要公开的卷影副本的卷影副本 ID。 你还可以使用现有的别名或环境变量来代替*shadowID*。 使用**add**而不使用参数查看现有别名。 |
| `<drive:>` | 将指定的卷影副本作为驱动器号公开（例如 `p:` ）。 |
| `<share>` | 公开共享中的指定卷影副本（例如 `\\machinename` ）。   |
| `<mountpoint>` | 向装入点公开指定的卷影副本（例如 `C:\shadowcopy` ）。 |

### <a name="examples"></a>示例

若要将与 VSS_SHADOW_1 环境变量关联的持久影子副本作为驱动器 X 公开，请键入：

```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diskshadow 命令](diskshadow.md)
