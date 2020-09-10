---
title: mountvol
description: 用于创建、删除或列出卷装入点的 mountvol 命令的参考文章。
ms.topic: reference
ms.assetid: fea8ad4d-f04a-4aaa-a3e5-75931e867b39
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4da7562bd50072dc91538bd08b5462222857830d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640131"
---
# <a name="mountvol"></a>mountvol

创建、删除或列出卷装入点。 你还可以链接卷，而无需使用驱动器号。

## <a name="syntax"></a>语法

```
mountvol [<drive>:]<path volumename>
mountvol [<drive>:]<path> /d
mountvol [<drive>:]<path> /l
mountvol [<drive>:]<path> /p
mountvol /r
mountvol [/n|/e]
mountvol <drive>: /s
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[<drive>:]<path>` | 指定装入点将驻留的现有 NTFS 目录。 |
| `<volumename>` | 指定作为装入点目标的卷名称。 卷名使用以下语法，其中 *GUID* 是全局唯一标识符： `\\?\volume\{GUID}\` 。 需要括号 `{ }` 。 |
| /d | 从指定的文件夹中删除卷装入点。 |
| /l | 列出指定文件夹的已装入卷名。 |
| /p | 从指定的目录中删除卷装入点，卸载基本卷，并使基本卷脱机，使其不可装入。 如果其他进程正在使用该卷，则 **mountvol** 会在卸载卷之前关闭任何打开的句柄。 |
| /r | 删除不再位于系统中的卷的卷装入点目录和注册表设置，阻止它们自动装载，并在将其添加回系统时，将其指定为其以前的卷装入点 () 。 |
| /n | 禁用新基本卷的自动装载。 添加到系统时，不会自动装载新卷。 |
| /e | 重新启用新基本卷的自动装载。 |
| /s | 将 EFI 系统分区装载到指定驱动器上。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

- 如果在使用 **/p** 参数时卸除卷，则卷列表将在创建卷装入点之前，将卷显示为 "未装入"。

- 如果卷有多个装入点，请使用 **/d** 在使用 **/p**之前删除其他装入点。 可以通过分配卷装入点，使基本卷再次可装入。

- 如果你需要扩展卷空间而不重新格式化或更换硬盘驱动器，则可以将装入路径添加到另一个卷。 将一个卷与多个装载路径一起使用的好处是，你可以使用单个驱动器号 (例如) 来访问所有本地卷 `C:` 。 你不需要记住哪个卷与哪个驱动器号相对应，但你仍可以装载本地卷并为其分配驱动器号。

## <a name="examples"></a>示例

若要创建装入点，请键入：

```
mountvol \sysmount \\?\volume\{2eca078d-5cbc-43d3-aff8-7e8511f60d0e}\
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
