---
title: convert mbr
description: 用于转换 mbr 的 Windows 命令主题，该主题将具有 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eeaf79a380fb5f1074d2bbef004537804caa0d8d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847200"
---
# <a name="convert-mbr"></a>convert mbr

将具有 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。

> [!IMPORTANT]
> 磁盘必须为空，才能将其转换为 MBR 磁盘。 转换磁盘之前，请备份数据，然后删除全部分区或卷。

有关如何使用此命令的说明，请参阅[将 GUID 分区表磁盘更改为主启动记录磁盘](https://go.microsoft.com/fwlink/?LinkId=207050)（ https://go.microsoft.com/fwlink/?LinkId=207050)。

## <a name="syntax"></a>语法

```
convert mbr [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   若要成功执行此操作，必须选择基本磁盘。 使用 "**选择磁盘**" 命令选择基本磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将基本光盘从 GPT 分区形式转换为 MBR 分区形式，请键入 >：
```
convert mbr
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

