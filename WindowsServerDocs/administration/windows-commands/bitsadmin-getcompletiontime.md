---
title: bitsadmin getcompletiontime
description: 适用于**bitsadmin getcompletiontime**的 Windows 命令主题，用于检索作业传输数据完成的时间。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7a4b3c1c-9832-4724-86b2-cce3c01bfa28
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5408e7e8c35135601a4a0af0ab7e9c55cea4c8dd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850750"
---
# <a name="bitsadmin-getcompletiontime"></a>bitsadmin getcompletiontime

检索作业传输数据完成的时间。

## <a name="syntax"></a>语法

```
bitsadmin /getcompletiontime <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业完成传输数据的时间。

```
C:\>bitsadmin /getcompletiontime myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)