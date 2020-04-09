---
title: bitsadmin getvalidationstate
description: 适用于**bitsadmin getvalidationstate**的 Windows 命令主题，它报告作业中给定文件的内容验证状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 52d7d983cc7858607c350483ed81223d107cee25
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850430"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate

报告作业中给定文件的内容验证状态。

## <a name="syntax"></a>语法

```
bitsadmin /getvalidationstate <job> <file_index>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例获取名为*myDownloadJob*的作业中的文件2的内容验证状态。

```
C:\>bitsadmin /getvalidationstate myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)