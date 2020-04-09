---
title: bitsadmin getfilestransferred
description: 适用于**bitsadmin getfilestransferred**的 Windows 命令主题，用于检索为指定作业传输的文件数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 053b67f5f85066d202b446b31eb1b1698fd735b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850670"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

检索指定的作业传输的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为作业中传输的文件数 *myDownloadJob*。

```
C:\>bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)