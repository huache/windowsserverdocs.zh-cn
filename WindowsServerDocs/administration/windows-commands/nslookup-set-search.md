---
title: nslookup set search
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9972919eae1be21d5dd30820d64dd1576b935666
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838300"
---
# <a name="nslookup-set-search"></a>nslookup set search



向请求追加 DNS 域搜索列表中的域名系统（DNS）域名，直到接收到答案。 这适用于以下情况：集和查找请求至少包含一个句点，但不以尾随句点结束。

## <a name="syntax"></a>语法

```
set [no]search
```

### <a name="parameters"></a>参数

|  参数   |                                                                          说明                                                                          |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **nosearch** |                            停止将 DNS 域搜索列表中的域名系统（DNS）域名追加到该请求。                            |
|  **寻找**  | 向请求追加 DNS 域搜索列表中的域名系统（DNS）域名，直到接收到答案。 默认语法为 "**搜索**"。 |
|    {帮助     |                                                                              ?}                                                                               |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)