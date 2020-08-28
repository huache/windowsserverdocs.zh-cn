---
title: nslookup set srchlist
description: Nslookup set srchlist 命令的参考文章，此命令会将默认域名系统 (DNS) 域名和搜索列表更改。
ms.topic: reference
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45f829337cca347b1503aca0fb02a1c77359914a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037285"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改默认域名系统 (DNS) 域名和搜索列表。 此命令替代 [nslookup set 域](nslookup-set-domain.md) 命令的默认 DNS 域名和搜索列表。

## <a name="syntax"></a>语法

```
set srchlist=<domainname>[/...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 为默认 DNS 域和搜索列表指定新名称。 默认域名值基于主机名。 最多可以指定六个名称之间用斜杠分隔 (/) 。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 使用 [nslookup "全部设置](nslookup-set-all.md) " 命令来显示列表。

### <a name="examples"></a>示例

若要将 DNS 域设置为 *mfg.widgets.com* ，并将搜索列表设置为三个名称：

```
set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set domain](nslookup-set-domain.md)

- [nslookup set all](nslookup-set-all.md)
