---
title: nslookup root
description: Nslookup 根命令的参考文章，该命令会将默认服务器更改为域名系统的根服务器 (DNS) 域名空间。
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 708c30f8915b422dd12c38a25fd07d62c27ea268
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885817"
---
# <a name="nslookup-root"></a>nslookup root

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将默认服务器更改为域名系统的根服务器 (DNS) 域名空间。 目前，使用了 ns.nic.ddn.mil 名称服务器。 可以使用[nslookup set root](nslookup-set-root.md)命令更改根服务器的名称。

> [!NOTE]
> 此命令与相同 `lserver ns.nic.ddn.mil` 。

## <a name="syntax"></a>语法

```
root
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set root](nslookup-set-root.md)
