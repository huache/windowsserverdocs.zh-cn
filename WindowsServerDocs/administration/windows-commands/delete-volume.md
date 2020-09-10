---
title: delete volume
description: 删除卷命令的参考文章，用于删除选定的卷。
ms.topic: reference
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 66793e9d7c22b337164807bf76ee82c10d70547c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628799"
---
# <a name="delete-volume"></a>delete volume

删除所选的卷。 在开始之前，你必须选择一个卷才能使此操作成功。 使用 " [选择音量](select-volume.md) " 命令选择卷并将焦点移动到该卷。

> [!IMPORTANT]
> 不能删除系统卷、启动卷或任何包含活动页面文件或故障转储 (内存转储) 的卷。

## <a name="syntax"></a>语法

```
delete volume [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要删除具有焦点的卷，请键入：

```
delete volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [select volume](select-volume.md)

- [删除命令](delete.md)