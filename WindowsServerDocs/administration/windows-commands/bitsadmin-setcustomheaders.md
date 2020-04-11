---
title: bitsadmin setcustomheaders
description: 适用于**bitsadmin setcustomheaders**的 Windows 命令主题，该主题将自定义 HTTP 标头添加到 GET 请求。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5b1a28f03815a22a3f8d10b2c3d1d4a3a2ae635
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123028"
---
# <a name="bitsadmin-setcustomheaders"></a>bitsadmin setcustomheaders

向发送到 HTTP 服务器的 GET 请求添加自定义 HTTP 标头。

## <a name="syntax"></a>语法

```
bitsadmin /setcustomheaders <job> <header1> <header2> <...>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| `<header1> <header2>` 等 | 作业的自定义标头。 |

## <a name="examples"></a>示例

以下示例添加名为*myDownloadJob*的作业的自定义 HTTP 标头。 有关 GET 请求的详细信息，请参阅[方法定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3)和[标头字段定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)。

```
C:\>bitsadmin /setcustomheaders myDownloadJob accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)