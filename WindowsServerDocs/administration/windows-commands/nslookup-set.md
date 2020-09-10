---
title: nslookup set
description: 用于更改影响查找行为方式的配置设置的 nslookup set 命令的参考文章。
ms.topic: reference
ms.assetid: 1fe5b36d-e93e-468b-abca-43b0204b32d1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 70850cd40f7eb54212b112a6e1410a25628a3d7f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636472"
---
# <a name="nslookup-set"></a>nslookup set

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改影响查找功能的配置设置。

## <a name="syntax"></a>语法

```
set all [class | d2 | debug | domain | port | querytype | recurse | retry | root | search | srchlist | timeout | type | vc] [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [nslookup set all](nslookup-set-all.md) | 列出所有当前设置。 |
| [nslookup set class](nslookup-set-class.md) | 更改查询类，该类指定信息的协议组。 |
| [nslookup set d2](nslookup-set-d2.md) | 打开或关闭详细调试模式。 |
| [nslookup set debug](nslookup-set-debug.md) | 完全关闭调试模式。 |
| [nslookup set domain](nslookup-set-domain.md) | 将默认域名系统 (DNS) 域名更改为指定名称。 |
| [nslookup set port](nslookup-set-port.md) | 将默认的 TCP/UDP 域名系统 (DNS) 名称服务器端口更改为指定值。
| [nslookup set querytype](nslookup-set-querytype.md) | 更改查询的资源记录类型。 |
| [nslookup set recurse](nslookup-set-recurse.md) | 告诉域名系统 (DNS) 名称服务器在找不到任何信息时查询其他服务器。 |
| [nslookup set retry](nslookup-set-retry.md) | 设置重试次数。 |
| [nslookup set root](nslookup-set-root.md) | 更改用于查询的根服务器的名称。 |
| [nslookup set search](nslookup-set-search.md) | 将 DNS 域搜索列表中的域名系统 (DNS) 域名追加到请求，直到收到答案。 |
| [nslookup set srchlist](nslookup-set-srchlist.md) | 更改默认域名系统 (DNS) 域名和搜索列表。 |
| [nslookup set timeout](nslookup-set-timeout.md) | 更改等待查找请求回复的初始秒数。 |
| [nslookup set type](nslookup-set-type.md) | 更改查询的资源记录类型。 |
| [nslookup set vc](nslookup-set-vc.md) | 指定将请求发送到服务器时是否使用虚拟线路。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
