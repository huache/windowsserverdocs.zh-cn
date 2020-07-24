---
title: online disk
description: 联机磁盘命令的参考文章，该命令使脱机磁盘进入联机状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bc44a783-eaa4-40ca-be01-5703b5bf4eb3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b8b5dc2ec454cd98eb4b03952a400815f4e7ea3b
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956699"
---
# <a name="online-disk"></a>online disk

使脱机磁盘进入联机状态。 对于基本磁盘，此命令尝试使所选磁盘和该磁盘上的所有卷联机。 对于动态磁盘，此命令会尝试将未标记为 "外部" 的所有磁盘都置于本地计算机上。 它还尝试使动态磁盘集上的所有卷联机。

如果磁盘组中的动态磁盘处于联机状态，并且它是组中的唯一磁盘，则会重新创建原始组，并将磁盘移到该组。 如果组中有其他磁盘并且它们处于联机状态，则磁盘只会重新添加到组中。 如果选定磁盘的组包含镜像卷或 RAID-5 卷，此命令还会重新同步这些卷。

> [!NOTE]
> 必须选择磁盘才能使**联机磁盘**命令成功。 使用 "[选择磁盘](select-disk.md)" 命令选择磁盘，并将焦点移动到该磁盘。

> [!IMPORTANT]
> 如果在只读磁盘上使用此命令，则此命令将失败。

## <a name="syntax"></a>语法

```
online disk [noerr]
```

### <a name="parameters"></a>参数

有关使用此命令的说明，请参阅[重新激活丢失或脱机的动态磁盘](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732026(v=ws.11))。

| 参数 | 说明 |
|--|--|
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要使具有焦点的磁盘联机，请键入：

```
online disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
