---
title: nslookup set search
description: Nslookup set search 命令的参考主题，它将 DNS 域搜索列表中的域名系统（DNS）域名追加到请求，直到收到答案。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c3219434f768a573c9e433c44b6b38bc9dc75f14
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721422"
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
| search | 将域名系统（DNS）域名追加到请求的 DNS 域搜索列表中，直到接收到答案。 这是默认值。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
