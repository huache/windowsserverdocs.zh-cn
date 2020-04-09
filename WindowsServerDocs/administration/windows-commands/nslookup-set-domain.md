---
title: nslookup set domain
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fa433383e23fd19779960348e0af88e0a405ff83
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838460"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将默认域名系统（DNS）域名改为指定的名称。
## <a name="syntax"></a>语法
```
set domain=<DomainName>
```
### <a name="parameters"></a>参数

|    参数    |                                           说明                                           |
|-----------------|-------------------------------------------------------------------------------------------------|
|  <DomainName>   | 为默认 DNS 域名指定新名称。 默认域名为主机名。 |
| {help &#124; ？} |                      显示**nslookup**子命令的简短摘要。                      |

## <a name="remarks"></a>备注
- 根据**bre-walkthrough-defname**和**搜索**选项的状态，将默认 DNS 域名追加到查找请求。 如果 DNS 域搜索列表中至少有两个组件的名称，则它包含默认 DNS 域的父项。 例如，如果默认 DNS 域为 mfg.widgets.com，则搜索列表将被命名为 mfg.widgets.com 和 widgets.com。 使用**set srchlist**命令指定其他列表，并使用 "**全部设置**" 命令来显示列表。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [nslookup 集 srchlist](nslookup-set-srchlist.md)
  [nslookup 集全部](nslookup-set-all.md)
