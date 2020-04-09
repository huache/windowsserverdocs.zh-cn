---
title: nslookup lserver
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d0d8619101d2e7b1f7fb6d6ed99d801c7c264f1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838630"
---
# <a name="nslookup-lserver"></a>nslookup lserver

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将默认服务器更改为指定的域名系统（DNS）域。
## <a name="syntax"></a>语法
```
lserver <DNSDomain> 
```
### <a name="parameters"></a>参数

|    参数    |                      说明                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | 为默认服务器指定新的 DNS 域。  |
| {help &#124; ？} | 显示**nslookup**子命令的简短摘要。 |

## <a name="remarks"></a>备注
- **Lserver**命令使用初始服务器来查找有关指定 DNS 域的信息。 这与**服务器**命令不同，后者使用当前的默认服务器。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [nslookup 服务器](nslookup-server.md)
