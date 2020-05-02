---
title: nslookup lserver
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2054c0fd427b41e7d6076258b29ab78d0fb7892
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723677"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将默认服务器更改为指定的域名系统（DNS）域。
## <a name="syntax"></a>语法
```
lserver <DNSDomain> 
```
### <a name="parameters"></a>参数

|    参数    |                      描述                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | 为默认服务器指定新的 DNS 域。  |
| {help &#124;？} | 显示**nslookup**子命令的简短摘要。 |

## <a name="remarks"></a>备注
- **Lserver**命令使用初始服务器来查找有关指定 DNS 域的信息。 这与**服务器**命令不同，后者使用当前的默认服务器。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法 Key](command-line-syntax-key.md)
  [nslookup 服务器](nslookup-server.md)
