---
title: nslookup server
description: Nslookup 服务器命令的参考文章，该命令会将默认服务器更改为指定的域名系统 (DNS) 域。
ms.topic: reference
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32450197fe7d3c04258b7fb3f77f8e17cd1c113e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038758"
---
# <a name="nslookup-server"></a>nslookup server

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

 (DNS) 域将默认服务器更改为指定的域名系统。

此命令使用当前默认服务器来查找有关指定 DSN 域的信息。 如果要使用初始服务器查找信息，请使用 [nslookup lserver](nslookup-lserver.md) 命令。

## <a name="syntax"></a>语法

```
server <DNSdomain>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<DNSdomain>` | 指定默认服务器的 DNS 域。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup lserver](nslookup-lserver.md)
