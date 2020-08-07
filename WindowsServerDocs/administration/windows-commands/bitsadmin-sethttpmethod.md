---
title: bitsadmin sethttpmethod
description: Bitsadmin sethttpmethod 命令的参考文章，用于设置要使用的 HTTP 谓词。
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 9b782ea4f07113541ce62eaef63ac8047141e766
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881040"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

设置要使用的 HTTP 谓词。

## <a name="syntax"></a>语法

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| httpmethod | 要使用的 HTTP 谓词。 有关可用谓词的信息，请参阅[方法定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
