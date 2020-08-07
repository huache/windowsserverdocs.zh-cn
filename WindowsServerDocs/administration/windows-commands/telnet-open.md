---
title: telnet open
description: 用于连接到 telnet 服务器的 telnet 开放式参考文章。
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 11498b2d2f38b96725608e6e72d30d0d563fd88a
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881699"
---
# <a name="telnet-open"></a>telnet：打开

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

连接到 telnet 服务器。

## <a name="syntax"></a>语法
```
o[pen] <hostname> [<Port>]
```
#### <a name="parameters"></a>参数

| 参数  |                                        描述                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         指定计算机名称或 IP 地址。                         |
|  [<Port>]  | 指定 telnet 服务器正在侦听的 TCP 端口。 默认值为 TCP 端口23。 |

## <a name="examples"></a>示例
在 telnet.microsoft.com 连接到 telnet 服务器。
```
o telnet.microsoft.com
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
