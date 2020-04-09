---
title: clean
description: 用于 Diskpart clean 命令的 Windows 命令主题，它从具有焦点的磁盘中删除所有分区或卷格式。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d573a0480c24a2a622618197dea7dccaeddac271
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847750"
---
# <a name="clean"></a>clean

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Diskpart clean 命令从具有焦点的磁盘中删除所有分区或卷格式。

## <a name="syntax"></a>语法
```
clean [all]
```
### <a name="parameters"></a>参数

| 参数 |                                                        说明                                                        |
|-----------|---------------------------------------------------------------------------------------------------------------------------|
|    全部    | 指定磁盘上的每个扇区都设置为零，这会完全删除磁盘上包含的所有数据。 |

## <a name="remarks"></a>备注
- 在主启动记录 (MBR) 磁盘中，只覆盖 MBR 分区信息和隐藏的扇区信息。
- 在 GUID 分区表（gpt）磁盘上，将覆盖 gpt 分区信息（包括保护 MBR）。 没有隐藏扇区信息。
- 若要成功执行此操作，必须选择磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例
  若要从所选磁盘中删除所有格式设置，请键入：
  ```
  clean
  ```

## <a name="additional-references"></a>其他参考
[清除磁盘](https://technet.microsoft.com/library/hh848661.aspx)
