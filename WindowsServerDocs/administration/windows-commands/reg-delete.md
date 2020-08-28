---
title: reg delete
description: 用于从注册表中删除子项的注册表项的引用项目。
ms.topic: reference
ms.assetid: cee05071-1607-4ab1-b8ab-65caebeb85c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08eea4b5cf330dda64406704fee390868c96c7a4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033775"
---
# <a name="reg-delete"></a>reg delete

删除注册表中的一个或一些项。

## <a name="syntax"></a>语法

```
reg delete <keyname> [{/v Valuename | /ve | /va}] [/f]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname1>` | 指定要添加的子项或项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /v `<Valuename>` | 删除子项下的特定项。 如果未指定任何项，则将删除子项下的所有项和子项。 |
| /ve | 指定仅删除没有值的条目。 |
| /va | 删除指定子项下的所有条目。 不会删除指定子项下的子项。 |
| /f | 删除现有的注册表子项或条目，而不要求确认。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- **Reg delete**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

### <a name="examples"></a>示例

若要删除注册表项超时及其所有子项和值，请键入：

```
reg delete HKLM\Software\MyCo\MyApp\Timeout
```

若要在名为天干地支的计算机上的 HKLM\Software\MyCo 下删除注册表值 MTU，请键入：

```
reg delete \\ZODIAC\HKLM\Software\MyCo /v MTU
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
