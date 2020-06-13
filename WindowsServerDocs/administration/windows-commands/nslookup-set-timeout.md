---
title: nslookup set timeout
description: Nslookup set timeout 命令的参考主题，它更改等待查找请求回复的初始秒数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d8fd0d96226e193ba723cc0a726ddf5362a538c
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721382"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改等待查找请求回复的初始秒数。 如果在指定的时间内未收到答复，则超时期限将加倍，并重新发送请求。 使用[nslookup set retry](nslookup-set-retry.md)命令确定尝试发送请求的次数。

## <a name="syntax"></a>语法

```
set timeout=<number>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| `<number>` | 指定等待答复的秒数。 默认等待的秒数为**5**。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要设置将响应时间设置为2秒的超时值：

```
set timeout=2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set retry](nslookup-set-retry.md)
