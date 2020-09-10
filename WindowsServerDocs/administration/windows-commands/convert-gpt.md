---
title: convert gpt
description: 转换 gpt 命令的参考文章：将具有主启动记录的空白基本磁盘转换 (MBR) 分区形式转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。
ms.topic: reference
ms.assetid: b3b1b747-0a7a-4be2-8487-2c4be16ee190
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 040bf89e020076e923f01f5cd20450c7d7fb820a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629313"
---
# <a name="convert-gpt"></a>convert gpt

将具有主启动记录 (MBR) 分区形式的空白基本磁盘转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。 必须选择基本 MBR 磁盘，此操作才能成功。 使用 " [选择磁盘" 命令](select-disk.md) 选择基本磁盘，并将焦点移动到该磁盘。

> [!IMPORTANT]
> 若要将磁盘转换成基本磁盘，该磁盘必须为空。 转换磁盘之前，请备份数据，然后删除全部分区或卷。 转换为 GPT 所需的最小磁盘大小为 128 mb。

> [!NOTE]
> 有关如何使用此命令的说明，请参阅 [将主启动记录磁盘更改为 GUID 分区表磁盘](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc725671(v=ws.11))。

## <a name="syntax"></a>语法

```
convert gpt [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要将基本光盘从 MBR 分区形式转换为 GPT 分区形式，请键入：

```
convert gpt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [转换命令](convert.md)
