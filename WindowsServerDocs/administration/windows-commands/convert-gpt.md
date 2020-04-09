---
title: convert gpt
description: 用于转换 gpt 的 Windows 命令主题，该主题将具有主启动记录（MBR）分区形式的空白基本磁盘转换为具有 GUID 分区表（GPT）分区形式的基本磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b3b1b747-0a7a-4be2-8487-2c4be16ee190
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c1ffe61245f7752ccc81d21d513fa00acd7b68b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847280"
---
# <a name="convert-gpt"></a>convert gpt

将具有主启动记录 (MBR) 分区形式的空白基本磁盘转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。

有关如何使用此命令的说明，请参阅[将主启动记录磁盘更改为 GUID 分区表磁盘](https://go.microsoft.com/fwlink/?LinkId=207049)（ https://go.microsoft.com/fwlink/?LinkId=207049)。

## <a name="syntax"></a>语法

```
convert gpt [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

> [!IMPORTANT]
> 磁盘必须为空，才能将其转换为 GPT 磁盘。 转换磁盘之前，请备份数据，然后删除全部分区或卷。
> -   转换为 GPT 所需的最小磁盘大小为 128 mb。
> -   必须选择基本 MBR 磁盘，此操作才能成功。 使用 "**选择磁盘**" 命令选择基本磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将基本光盘从 MBR 分区形式转换为 GPT 分区形式，请键入：
```
convert gpt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

