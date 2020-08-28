---
title: nslookup set retry
description: Nslookup set retry 命令的参考文章，用于设置尝试从指定服务器获取信息的次数。
ms.topic: reference
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 10f60b48485ae51d727f17a5cfcec8b2af61a743
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025171"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

如果在特定时间段内未收到答复，则超时期限将加倍，并重新发送请求。 此命令在放弃之前，将请求重新发送到服务器以获取信息的次数。

> [!NOTE]
> 若要更改请求超时前的时间长度，请使用 [nslookup set timeout](nslookup-set-timeout.md) 命令。

## <a name="syntax"></a>语法

```
set retry=<number>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| `<number>` | 指定重试次数的新值。 默认重试次数为 **4**。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set timeout](nslookup-set-timeout.md)
