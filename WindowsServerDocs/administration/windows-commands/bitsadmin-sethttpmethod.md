---
title: bitsadmin sethttpmethod
description: Bitsadmin sethttpmethod 命令的参考文章，用于设置要使用的 HTTP 谓词。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 8374a8e306f88cbdbad079d99233171712cc00bc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026265"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

设置要使用的 HTTP 谓词。

## <a name="syntax"></a>语法

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| httpmethod | 要使用的 HTTP 谓词。 有关可用谓词的信息，请参阅 [方法定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
