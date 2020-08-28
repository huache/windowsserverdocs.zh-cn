---
title: reg load
description: Reg load 命令的参考文章，可将保存的子项和条目写入注册表中的不同子项。
ms.topic: reference
ms.assetid: 3b0b2b1b-f510-4108-9e9d-7057e924aa6e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8647b417999459b210986187bd523b3953a8b2d6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028025"
---
# <a name="reg-load"></a>reg load

将保存的子项和项写入注册表中的不同子项。 此命令适用于用于排查或编辑注册表项的临时文件。

## <a name="syntax"></a>语法

```
reg load <keyname> <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname>` | 指定要加载的子项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。  |
| `<filename>` | 指定要加载的文件的名称和路径。 必须使用 **reg save** 命令提前创建此文件，并且该文件的扩展名必须为 hiv。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- **Reg load**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要将名为 hiv 的文件加载到密钥 HKLM\TempHive，请键入：

```
reg load HKLM\TempHive TempHive.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [reg save 命令](reg-save.md)
