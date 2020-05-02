---
title: clean
description: Diskpart clean 命令的参考主题，它从具有焦点的磁盘中删除所有分区或卷格式。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45a23919dc07c8c1525808859471fdcb9f9e9403
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82712879"
---
# <a name="clean"></a>clean

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从具有焦点的磁盘中删除所有分区或卷格式。

>[!NOTE]
> 有关此命令的 PowerShell 版本，请参阅[明文命令](https://docs.microsoft.com/powershell/module/storage/clear-disk)。

## <a name="syntax"></a>语法

```
clean [all]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| all | 指定磁盘上的每个扇区都设置为零，这会完全删除磁盘上包含的所有数据。 |

#### <a name="remarks"></a>备注

- 在主启动记录（MBR）磁盘上，只覆盖 MBR 分区信息和隐藏扇区信息。

- 在 GUID 分区表（gpt）磁盘上，将覆盖 gpt 分区信息（包括保护 MBR）。 没有隐藏扇区信息。

- 若要成功执行此操作，必须选择磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a>示例

若要从所选磁盘中删除所有格式设置，请键入：

```
clean
```

## <a name="additional-references"></a>其他参考

- [清除磁盘命令](https://docs.microsoft.com/powershell/module/storage/clear-disk)

- [命令行语法项](command-line-syntax-key.md)
