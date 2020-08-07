---
title: offline volume
description: 脱机 volume 命令的参考文章，该命令会将具有焦点的联机卷置于脱机状态。
ms.topic: article
ms.assetid: b8f7192f-ea38-47d0-9d4e-58ef68336ae6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e8a6bbebb88f97c4e4b04afccedeb05c4a1392a
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885266"
---
# <a name="offline-volume"></a>offline volume

使具有焦点的联机卷进入脱机状态。

> [!NOTE]
> 必须选择卷才能使 "**脱机卷**" 命令成功。 使用 "[选择卷](select-volume.md)" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
offline volume [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要使具有焦点的磁盘脱机，请键入：

```
offline volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
