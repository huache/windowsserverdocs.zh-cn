---
title: bitsadmin sethttpmethod
description: Bitsadmin sethttpmethod 命令的参考文章，用于设置要使用的 HTTP 谓词。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 0c8d2357e35831db89365eabbe0b97cdec88b6aa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630871"
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
