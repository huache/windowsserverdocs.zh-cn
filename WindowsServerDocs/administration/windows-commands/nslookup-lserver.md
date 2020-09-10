---
title: nslookup lserver
description: Nslookup lserver 命令的参考文章，此命令将初始服务器更改为指定的域名系统 (DNS) 域。
ms.topic: reference
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d1f507b1a61e9fd4fc506fb4e74f869c83e95335
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635672"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将初始服务器更改为指定的域名系统 (DNS) 域。

此命令使用初始服务器来查找有关指定 DSN 域的信息。 如果要使用当前默认服务器查找信息，请使用 [nslookup 服务器](nslookup-server.md) 命令。

## <a name="syntax"></a>语法

```
lserver <DNSdomain>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<DNSdomain>` | 指定初始服务器的 DNS 域。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup server](nslookup-server.md)
