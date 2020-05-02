---
title: nslookup set srchlist
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8936daa3505b02295ae2f09c2910dead8d4c0ff8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723555"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改默认的域名系统（DNS）域名和搜索列表。

## <a name="syntax"></a>语法
```
Set srchlist=<DomainName>[/...]
```
### <a name="parameters"></a>参数

|    参数    |                                                                                        描述                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | 为默认 DNS 域和搜索列表指定新名称。 默认域名值基于主机名。 最多可以指定六个用斜杠（/）分隔的名称。 |
| {help &#124;？} |                                                                   显示**nslookup**子命令的简短摘要。                                                                   |

## <a name="remarks"></a>备注
- **Set srchlist**命令将覆盖**set domain**命令的默认 DNS 域名和搜索列表。 使用 "**全部设置**" 命令来显示列表。
  ## <a name="examples"></a>示例
  若要将 DNS 域设置为 mfg.widgets.com，并将搜索列表设置为三个名称：
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法密钥](command-line-syntax-key.md)
  [nslookup 设置域](nslookup-set-domain.md)
  [nslookup 全部设置](nslookup-set-all.md)
