---
title: nslookup set root
description: Nslookup set root 命令的参考主题，它更改了用于查询的根服务器的名称。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1271dbeb0381d01e70380bded82a94ba20163853
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721450"
---
# <a name="nslookup-set-root"></a>nslookup set root

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改用于查询的根服务器的名称。

> [!NOTE]
> 此命令支持[nslookup 根](nslookup-root.md)命令。

## <a name="syntax"></a>语法

```
set root=<rootserver>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| `<rootserver>` | 指定根服务器的新名称。 默认值为**ns.nic.ddn.mil**。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup root](nslookup-root.md)
