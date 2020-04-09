---
title: nslookup set querytype
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5af54ac5-fc1a-4af6-977b-f8e97c8eba90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1c066277a22325e5db8383f58cda31038aa656e0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838430"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改查询的资源记录类型。
## <a name="syntax"></a>语法
```
set querytype=<ResourceRecordtype>
```
### <a name="parameters"></a>参数
<ResourceRecordtype> 指定 DNS 资源记录类型。 默认资源记录类型是。下表列出了此命令的有效值。

| 值 |                                                   说明                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   A   |                                      指定计算机&#39;的 IP 地址                                      |
|  随时  |                                     指定计算机&#39;的 IP 地址。                                      |
| CNAME |                                    指定别名的规范名称。                                     |
|  GID  |                                  指定组名称的组标识符。                                  |
| HINFO |                          指定计算机&#39;的 CPU 和操作系统类型。                           |
|  MB   |                                        指定邮箱域名。                                         |
|  MG   |                                         指定邮件组成员。                                          |
| MINFO |                                   指定邮箱或邮件列表信息。                                   |
|  MR   |                                     指定邮件重命名域名。                                      |
|  MX   |                                          指定邮件交换器。                                          |
|  NS   |                                 指定命名区域的 DNS 名称服务器。                                 |
|  PTR  | 如果查询是 IP 地址，则指定计算机名;否则，指定指向其他信息的指针。 |
|  SOA  |                                指定 DNS 区域的授权。                                 |
|  TXT  |                                         指定文本信息。                                         |
|  标识号  |                                         指定用户标识符。                                          |
| UINFO |                                         指定用户信息。                                         |
|  WKS  |                                         描述一个众所周知的服务。                                         |
| {帮助 |                                                       ?}                                                        |

显示<strong>nslookup</strong>子命令的简短摘要
## <a name="remarks"></a>备注
- <strong>Set type</strong>命令执行与<strong>set querytype</strong>命令相同的功能。
- 有关资源记录类型的详细信息，请参阅请求注释（Rfc）1035。
  ## <a name="additional-references"></a>其他参考
  < href = key.md =-命令行语法[键](command-line-syntax-key.md)> 命令行语法键，</a> < href = nslookup =[nslookup 集类型](nslookup-set-type.md)> nslookup 集类型的数据源 = nslookup 集的类型</a>。
