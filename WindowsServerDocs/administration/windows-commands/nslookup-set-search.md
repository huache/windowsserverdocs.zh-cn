---
title: nslookup set search
description: "\"Nslookup 集搜索\" 命令的参考文章，将 DNS 域搜索列表中的域名系统（DNS）域名追加到请求，直到收到答案。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7b1740dd9bb3eb35c4cd1ef4890fcb977b2dc1ff
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935501"
---
# <a name="nslookup-set-search"></a>nslookup set search

向请求追加 DNS 域搜索列表中的域名系统（DNS）域名，直到接收到答案。 这适用于以下情况：集和查找请求至少包含一个句点，但不以尾随句点结束。

## <a name="syntax"></a>语法

```
set [no]search
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| nosearch | 停止在请求的 DNS 域搜索列表中追加域名系统（DNS）域名。 |
| 搜索 | 将域名系统（DNS）域名追加到请求的 DNS 域搜索列表中，直到接收到答案。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
