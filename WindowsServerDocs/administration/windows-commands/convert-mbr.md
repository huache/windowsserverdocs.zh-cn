---
title: convert mbr
description: 转换 mbr 命令的参考文章，将 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 784521c99e3fc0cf8d372f95424af785636a0687
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958509"
---
# <a name="convert-mbr"></a>convert mbr

将具有 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。 若要成功执行此操作，必须选择基本磁盘。 使用 "[选择磁盘" 命令](select-disk.md)选择基本磁盘，并将焦点移动到该磁盘。

> [!IMPORTANT]
> 若要将磁盘转换成基本磁盘，该磁盘必须为空。 转换磁盘之前，请备份数据，然后删除全部分区或卷。

> [!NOTE]
> 有关如何使用此命令的说明，请参阅[将 GUID 分区表磁盘更改为主启动记录磁盘](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc725797(v=ws.11))。

## <a name="syntax"></a>语法

```
convert mbr [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要将基本光盘从 GPT 分区形式转换为 MBR 分区形式，请键入>：

```
convert mbr
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [转换命令](convert.md)
