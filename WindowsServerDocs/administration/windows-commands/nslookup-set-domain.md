---
title: nslookup set domain
description: Nslookup set 域命令的参考文章，此命令将默认域名系统 (DNS) 域名更改为指定名称。
ms.topic: reference
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed002a7a6278d9bcd11a59c5708c723d7ffe91ef
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023441"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将默认域名系统 (DNS) 域名更改为指定名称。

## <a name="syntax"></a>语法

```
set domain=<domainname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 为默认 DNS 域名指定新名称。 默认值为主机的名称。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 根据 **bre-walkthrough-defname** 和 **搜索** 选项的状态，将默认 DNS 域名追加到查找请求。

- 如果 DNS 域搜索列表中至少有两个组件的名称，则它包含默认 DNS 域的父项。 例如，如果默认 DNS 域为 mfg.widgets.com，则搜索列表将被命名为 mfg.widgets.com 和 widgets.com。

- 使用 [nslookup set srchlist](nslookup-set-srchlist.md) 命令可以指定其他列表，使用 [nslookup 设置 all](nslookup-set-all.md) 命令来显示列表。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set srchlist](nslookup-set-srchlist.md)

- [nslookup set all](nslookup-set-all.md)
