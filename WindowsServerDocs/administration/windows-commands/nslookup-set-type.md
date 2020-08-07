---
title: nslookup set type
description: "\"Nslookup 集类型\" 命令的参考文章，可更改查询的资源记录类型。"
ms.topic: article
ms.assetid: 5248e314-fac1-413e-81dc-bbe0a0873ba5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b339f5dc809df1ad9f3301108169c65b02e63309
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885467"
---
# <a name="nslookup-set-type"></a>nslookup set type

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改查询的资源记录类型。 有关资源记录类型的信息，请参阅[征求意见 (Rfc) 1035](https://tools.ietf.org/html/rfc1035)。

> [!NOTE]
> 此命令与[nslookup set querytype](nslookup-set-querytype.md)命令相同。

## <a name="syntax"></a>语法

```
set type=<resourcerecordtype>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<resourcerecordtype>` | 指定 DNS 资源记录类型。 默认资源记录类型**是，但**您可以使用以下任何值：<ul><li>**答：** 指定计算机的 IP 地址。</li><li>**任何：** 指定计算机的 IP 地址。</li><li>**CNAME：** 指定别名的规范名称。</li><li>**GID**指定组名称的组标识符。</li><li>**HINFO：** 指定计算机的 CPU 和操作系统类型。</li><li>**MB：** 指定邮箱域名。</li><li>**MG：** 指定邮件组成员。</li><li>**MINFO：** 指定邮箱或邮件列表信息。</li><li>**MR：** 指定邮件重命名域名。</li><li>**MX：** 指定邮件交换器。</li><li>**NS：** 指定命名区域的 DNS 名称服务器。</li><li>**PTR：** 如果查询是 IP 地址，则指定计算机名;否则，指定指向其他信息的指针。</li><li>**SOA：** 指定 DNS 区域的授权。</li><li>**TXT：** 指定文本信息。</li><li>**UID：** 指定用户标识符。</li><li>**UINFO：** 指定用户信息。</li><li>**WKS：** 描述一个众所周知的服务。</li></ul> |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set type](nslookup-set-querytype.md)
