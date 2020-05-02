---
title: nslookup set type
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5248e314-fac1-413e-81dc-bbe0a0873ba5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a9ccc7dde40b93db5f331930bc405c98764483d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723536"
---
# <a name="nslookup-set-type"></a>nslookup set type

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改查询的资源记录类型。
## <a name="syntax"></a>语法
```
set type=<ResourceRecordtype>
```
### <a name="parameters"></a>参数
<ResourceRecordtype>指定 DNS 资源记录类型。 默认资源记录类型是。下表列出了此命令的有效值。

| 值 |                                                   描述                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   A   |                                      指定&#39;s IP 地址的计算机                                      |
|  ANY  |                                     指定计算机&#39;的 IP 地址。                                      |
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
|  UID  |                                         指定用户标识符。                                          |
| UINFO |                                         指定用户信息。                                         |
|  WKS  |                                         描述一个众所周知的服务。                                         |
| {帮助 |                                                       ?}                                                        |

显示<strong>nslookup</strong>子命令的简短摘要。
## <a name="remarks"></a>备注
- <strong>Set type</strong>命令执行与<strong>set querytype</strong>命令相同的功能。
- 有关资源记录类型的详细信息，请参阅请求注释（Rfc）1035。
  ## <a name="additional-references"></a>其他参考
  <href = key.md =-命令行语法[键](command-line-syntax-key.md)，请>命令行语法键</a> <href = nslookup =[nslookup set querytype](nslookup-set-querytype.md)>nslookup set querytype 的数据源数据源 = nslookup set。</a>
