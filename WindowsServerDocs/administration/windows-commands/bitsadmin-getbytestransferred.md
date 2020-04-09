---
title: bitsadmin getbytestransferred
description: 适用于**bitsadmin getbytestransferred**的 Windows 命令主题，它检索为指定作业传输的字节数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 957b3e60bf8a5e41b3964f4d762633472606654d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850770"
---
# <a name="bitsadmin-getbytestransferred"></a>bitsadmin getbytestransferred

检索为指定作业传输的字节数。

## <a name="syntax"></a>语法

```
bitsadmin /getbytestransferred <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例检索为名为*myDownloadJob*的作业传输的字节数。

```
C:\>bitsadmin /getbytestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)