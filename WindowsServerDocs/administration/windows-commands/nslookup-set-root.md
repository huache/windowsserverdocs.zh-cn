---
title: nslookup set root
description: Nslookup set root 命令的参考文章，它更改用于查询的根服务器的名称。
ms.topic: reference
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d7e1251b7e13320a77a4c59736a6bd985bd248af
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637482"
---
# <a name="nslookup-set-root"></a>nslookup set root

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改用于查询的根服务器的名称。

> [!NOTE]
> 此命令支持 [nslookup 根](nslookup-root.md) 命令。

## <a name="syntax"></a>语法

```
set root=<rootserver>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| `<rootserver>` | 指定根服务器的新名称。 默认值为 **ns.nic.ddn.mil**。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup root](nslookup-root.md)
