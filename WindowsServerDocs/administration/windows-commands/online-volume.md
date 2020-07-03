---
title: online volume
description: 在线 volume 命令的参考文章，使脱机卷进入联机状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5da073fd-578d-4691-ad0f-605ba66e0c7e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2378b4cbc4f0624a0f1d65c62337d4c1a856648c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933519"
---
# <a name="online-disk"></a>online disk

使脱机卷进入联机状态。 此命令适用于已失败、发生故障或处于失败冗余状态的卷。

> [!NOTE]
> 必须选择卷才能使 "**联机音量**" 命令成功。 使用 "[选择音量](select-volume.md)" 命令选择卷并将焦点移动到该卷。

> [!IMPORTANT]
> 如果在只读磁盘上使用此命令，则此命令将失败。

## <a name="syntax"></a>语法

```
online volume [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要使具有焦点的卷联机，请键入：

```
online volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
