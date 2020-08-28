---
title: add volume
description: "\"添加卷\" 命令的参考文章，将卷添加到卷影副本集，这是要进行卷影复制的卷集。"
ms.topic: reference
ms.assetid: b7d4d35d-8bda-46d2-8df5-eb598cecaaba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4cf64e98c498f16032963f0b09a5aec4df162452
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029435"
---
# <a name="add-volume"></a>add volume

将卷添加到卷影副本集，这是要进行卷影复制的卷集。 创建卷影副本时，环境变量会将别名链接到卷影 ID，因此别名随后可用于脚本编写。

卷一次添加一个。 每次添加卷时，系统都会对其进行检查，以确保 VSS 支持为该卷创建卷影副本。 稍后使用 **set 上下文** 命令可以使此检查无效。

创建卷影副本需要此命令。 如果不使用参数， **add volume 将** 在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
add volume <volume> [provider <providerid>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<volume>` | 指定要添加到卷影副本集的卷。 创建卷影副本至少需要一个卷。 |
| `[provider \<providerid>]` | 指定用于创建卷影副本的已注册提供程序的提供程序 ID。 如果未指定 **提供程序** ，则使用默认提供程序。 |

## <a name="examples"></a>示例

若要查看当前已注册的提供程序列表，请在 `diskshadow>` 提示符下键入：

```
list providers
```

以下输出显示一个提供程序，默认情况下将使用该提供程序：

```
* ProviderID: {b5946137-7b9f-4925-af80-51abd60b20d5}
        Type: [1] VSS_PROV_SYSTEM
        Name: Microsoft Software Shadow Copy provider 1.0
        Version: 1.0.0.7
        CLSID: {65ee1dba-8ff4-4a58-ac1c-3470ee2f376a}
1 provider registered.
```

若要将驱动器 C：添加到卷影副本集并分配名为 *System1*的别名，请键入：

```
add volume c: alias System1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [设置上下文命令](set-context.md)
