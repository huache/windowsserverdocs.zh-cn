---
title: bitsadmin gettemporaryname
description: 适用于**bitsadmin gettemporaryname**的 Windows 命令主题，它报告作业中给定文件的临时文件名。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c331ecf12cb02d34c76692158c79eafbe5691c5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850450"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

报告作业中给定文件的临时文件名。

## <a name="syntax"></a>语法

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例报告名为*myDownloadJob*的作业的文件2的临时文件名。

```
C:\>bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)