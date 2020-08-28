---
title: offline disk
description: "\"脱机磁盘\" 命令的参考文章，该命令会将具有焦点的联机磁盘置于脱机状态。"
ms.topic: reference
ms.assetid: 8fb9b3c3-0b2c-4192-a2e7-f706292653e3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 186acfaf297e6b94faf11a235f36082672524e75
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037245"
---
# <a name="offline-disk"></a>offline disk

使联机磁盘具有焦点，使其进入脱机状态。 如果磁盘组中的动态磁盘处于脱机状态，则磁盘的状态将更改为 " **丢失** "，组将显示处于脱机状态的磁盘。 缺少的磁盘将被移动到无效组。 如果动态磁盘是组中的最后一个磁盘，则磁盘的状态将更改为 " **脱机**"，并删除空组。

> [!NOTE]
> 必须选择磁盘，才能成功执行 **脱机磁盘** 命令。 使用 " [选择磁盘](select-disk.md) " 命令选择磁盘，并将焦点移动到该磁盘。
>
> 此命令也可通过将 SAN 模式更改为脱机，在 SAN online 模式下的磁盘上运行。

## <a name="syntax"></a>语法

```
offline disk [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要使具有焦点的磁盘脱机，请键入：

```
offline disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
