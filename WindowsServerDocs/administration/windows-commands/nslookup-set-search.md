---
title: nslookup set search
description: "\"Nslookup 集搜索\" 命令的参考文章，该命令会在 DNS 域搜索列表中追加域名系统 (DNS) 域名发送给请求，直到收到答案。"
ms.topic: reference
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17cee7cbc2112db346c91ab4a7b88264eff6a850
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025151"
---
# <a name="nslookup-set-search"></a>nslookup set search

将 DNS 域搜索列表中的域名系统 (DNS) 域名追加到请求，直到收到答案。 这适用于以下情况：集和查找请求至少包含一个句点，但不以尾随句点结束。

## <a name="syntax"></a>语法

```
set [no]search
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| nosearch | 停止在请求的 DNS 域搜索列表中追加域名系统 (DNS) 域名。 |
| 搜索 | 将域名系统追加到请求的 DNS 域搜索列表中的域名系统 (DNS) 域名，直到接收到答案。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
