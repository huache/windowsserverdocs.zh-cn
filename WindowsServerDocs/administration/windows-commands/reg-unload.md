---
title: reg unload
description: Reg unload 命令的参考文章，该命令删除使用 reg load 操作加载的注册表部分。
ms.topic: reference
ms.assetid: 1d07791d-ca27-454e-9797-27d7e84c5048
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5a94f4c3193a7096bd99d83a927ccb0b694d7faa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640309"
---
# <a name="reg-unload"></a>reg unload

删除使用 **reg load** 操作加载的注册表部分。

## <a name="syntax"></a>语法

```
reg unload <keyname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<keyname>` | 指定子项的完整路径。 若要指定远程计算机，请将计算机名称 (格式设置 `\\<computername>\` 为 *keyname*) 的格式。 如果省略，则 `\\<computername>\` 会使操作默认为本地计算机。 *Keyname*必须包含有效的根密钥。 本地计算机的有效根密钥为： **HKLM**、 **HKCU**、 **HKCR**、 **hku 开头**和 **HKCC**。 如果指定了远程计算机，则有效的根密钥为： **HKLM** 和 **hku 开头**。 如果注册表项名包含空格，则将该密钥名称括在引号中。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Reg 卸载**操作的返回值为：

    | “值” | 说明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 失败 |

## <a name="examples"></a>示例

若要在文件 HKLM 中卸载 hive TempHive，请键入：

```
reg unload HKLM\TempHive
```

> [!CAUTION]
> 不要直接编辑注册表，除非没有替代方法。 注册表编辑器会绕过标准安全措施，同时允许可能降低性能的设置、损坏系统，甚至要求你重新安装 Windows。 可以通过使用控制面板中的 "程序" 或 "Microsoft 管理控制台 (MMC) 来安全地更改大多数注册表设置。 如果必须直接编辑注册表，请首先对其进行备份。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [reg load 命令](reg-load.md)
