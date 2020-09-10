---
title: clean
description: Diskpart clean 命令的参考文章，可从具有焦点的磁盘中删除所有分区或卷格式。
ms.topic: reference
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 82026520c456c76823993d34a4fb09bcd4b79808
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629657"
---
# <a name="clean"></a>clean

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从具有焦点的磁盘中删除所有分区或卷格式。

>[!NOTE]
> 有关此命令的 PowerShell 版本，请参阅 [明文命令](/powershell/module/storage/clear-disk)。

## <a name="syntax"></a>语法

```
clean [all]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 全部 | 指定磁盘上的每个扇区都设置为零，这会完全删除磁盘上包含的所有数据。 |

#### <a name="remarks"></a>备注

- 在主启动记录 (MBR) 磁盘上，仅覆盖 MBR 分区信息和隐藏扇区信息。

- 在 GUID 分区表 (gpt) 磁盘上，将覆盖 gpt 分区信息（包括保护 MBR）。 没有隐藏扇区信息。

- 若要成功执行此操作，必须选择磁盘。 使用 " **选择磁盘** " 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a>示例

若要从所选磁盘中删除所有格式设置，请键入：

```
clean
```

## <a name="additional-references"></a>其他参考

- [清除磁盘命令](/powershell/module/storage/clear-disk)

- [命令行语法项](command-line-syntax-key.md)
