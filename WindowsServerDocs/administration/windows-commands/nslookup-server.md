---
title: nslookup server
description: Nslookup 服务器命令的参考文章，该命令会将默认服务器更改为指定的域名系统 (DNS) 域。
ms.topic: reference
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 64d1383dd5c4fa86a62fad91bae0ed5e4eb1454b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635626"
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
