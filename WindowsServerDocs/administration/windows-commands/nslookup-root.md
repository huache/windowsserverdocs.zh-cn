---
title: nslookup root
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d11179ff3cd22acd9df67261e7ab752aa159201a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838640"
---
# <a name="nslookup-root"></a>nslookup root

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将服务器的默认服务器更改为域名系统（DNS）域名空间的根。
## <a name="syntax"></a>语法
```
root 
```
### <a name="parameters"></a>参数

|    参数    |                      说明                      |
|-----------------|-------------------------------------------------------|
| {help &#124; ？} | 显示**nslookup**子命令的简短摘要。 |

## <a name="remarks"></a>备注
- 目前，使用了 ns.nic.ddn.mil 名称服务器。 此命令是 lserver ns.nic.ddn.mil 的同义词。 可以通过 "**设置根**" 命令更改根服务器的名称。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [nslookup 集根](nslookup-set-root.md)
