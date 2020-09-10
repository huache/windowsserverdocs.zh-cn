---
title: bitsadmin setcustomheaders
description: Bitsadmin setcustomheaders 命令的参考文章，可将自定义 HTTP 标头添加到 GET 请求。
ms.topic: reference
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 06e6e580a92f96cbf8588d55ebeb44858174d29c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630989"
---
# <a name="bitsadmin-setcustomheaders"></a>bitsadmin setcustomheaders

向发送到 HTTP 服务器的 GET 请求添加自定义 HTTP 标头。 有关 GET 请求的详细信息，请参阅 [方法定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3) 和 [标头字段定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)。

## <a name="syntax"></a>语法

```
bitsadmin /setcustomheaders <job> <header1> <header2> <...>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| `<header1> <header2>` 依此类推 | 作业的自定义标头。 |

## <a name="examples"></a>示例

若要为名为 *myDownloadJob*的作业添加自定义 HTTP 标头：

```
bitsadmin /setcustomheaders myDownloadJob accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
