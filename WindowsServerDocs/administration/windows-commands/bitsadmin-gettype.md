---
title: bitsadmin gettype
description: '**Bitsadmin gettype**的 Windows 命令主题，它检索指定作业的作业类型。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 66a1fc5b0478e1eec26557dc9a7f76d50abcb8b6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850440"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype

检索指定作业的作业类型。

## <a name="syntax"></a>语法

```
bitsadmin /gettype <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="output"></a>Output

输出值包括：

| 类型 | 说明 |
| --------------- | ----------- |
| 下载 | 作业是一种下载。 |
| 上载 | 作业是上传。 |
| 上传-答复 | 作业是上传-答复。 |
| 未知 | 作业的类型未知。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业的作业类型。

```
C:\>bitsadmin /gettype myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)