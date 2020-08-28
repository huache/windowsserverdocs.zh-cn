---
title: attributes disk
description: "\"属性\" 磁盘命令的参考文章，其中显示、设置或清除磁盘的属性。"
ms.topic: reference
ms.assetid: eed57071-c1c6-4394-9542-62b52a878c92
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72b4a99c36085062441a7a8751a065dad1dd0c51
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029195"
---
# <a name="attributes-disk"></a>attributes disk

显示、设置或清除磁盘的属性。 使用此命令显示磁盘的当前属性时，"启动磁盘" 属性表示用于启动计算机的磁盘。 对于动态镜像，它会显示包含启动卷的启动丛的磁盘。

> [!IMPORTANT]
> 必须选择磁盘，"属性" **磁盘** 命令才能成功。 使用 " **选择磁盘** " 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
attributes disk [{set | clear}] [readonly] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| set | 设置具有焦点的磁盘的指定属性。 |
| clear | 清除具有焦点的磁盘的指定属性。 |
| readonly | 指定磁盘为只读。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要查看所选磁盘的属性，请键入：

```
attributes disk
```

若要将所选磁盘设置为只读，请键入：

```
attributes disk set readonly
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择磁盘命令](select-disk.md)
