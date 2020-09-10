---
title: '恢复 (DiskPart) '
description: 有关 DiskPart recover 命令的参考文章，该命令刷新磁盘组中所有磁盘的状态，尝试恢复无效磁盘组中的磁盘，并重新同步镜像卷和具有陈旧数据的 RAID-5 卷。
ms.topic: reference
ms.assetid: 8cc3a73d-9456-41a0-b375-2b4cc37c3992
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 55b31333f03ec90ba9c37b7d2e31c251893b18d8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637261"
---
# <a name="recover-diskpart"></a>恢复 (DiskPart) 

刷新磁盘组中所有磁盘的状态，尝试恢复无效磁盘组中的磁盘，并重新同步已过时的镜像卷和 RAID-5 卷。 此命令在失败或失败的磁盘上操作。 它还对失败、失败或处于失败状态的卷进行操作。

此命令对动态磁盘组进行操作。 如果对具有基本磁盘的组使用此命令，则不会返回错误，而不会执行任何操作。

> [!NOTE]
> 若要成功执行此操作，必须选择磁盘组中的磁盘。 使用 " [选择磁盘" 命令](select-disk.md) 选择磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
recover [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要恢复包含焦点磁盘的磁盘组，请键入：

```
recover
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
