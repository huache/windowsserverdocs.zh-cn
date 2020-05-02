---
title: nslookup set search
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e3f5bce42d3614b535b2dfb00c4c9ea9cac2346
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723568"
---
# <a name="nslookup-set-search"></a>nslookup set search



向请求追加 DNS 域搜索列表中的域名系统（DNS）域名，直到接收到答案。 这适用于以下情况：集和查找请求至少包含一个句点，但不以尾随句点结束。

## <a name="syntax"></a>语法

```
set [no]search
```

### <a name="parameters"></a>参数

|  参数   |                                                                          描述                                                                          |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **nosearch** |                            停止将 DNS 域搜索列表中的域名系统（DNS）域名追加到该请求。                            |
|  **寻找**  | 向请求追加 DNS 域搜索列表中的域名系统（DNS）域名，直到接收到答案。 默认语法为 "**搜索**"。 |
|    {帮助     |                                                                              ?}                                                                               |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)