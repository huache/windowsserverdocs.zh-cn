---
title: bitsadmin gettype
description: Bitsadmin gettype 命令的参考文章，它检索指定作业的作业类型。
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3f0fe66256e59526b874aaf2ec8ae0193846a1da
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893821"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype

检索指定作业的作业类型。

## <a name="syntax"></a>语法

```
bitsadmin /gettype <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>Output

返回的输出值可以是：

| 类型 | 说明 |
| --------------- | ----------- |
| 下载 | 作业是一种下载。 |
| 上载 | 作业是上传。 |
| 上传-答复 | 作业是上传-答复。 |
| 未知 | 作业的类型未知。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的作业类型：

```
bitsadmin /gettype myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
