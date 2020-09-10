---
title: nslookup root
description: Nslookup 根命令的参考文章，该命令会将默认服务器更改为域名系统的根服务器 (DNS) 域名空间。
ms.topic: reference
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e3dbbdf970143ce1e82f0c817fc1f53c5b22749
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635651"
---
# <a name="nslookup-root"></a>nslookup root

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将默认服务器更改为域名系统的根服务器 (DNS) 域名空间。 目前，使用了 ns.nic.ddn.mil 名称服务器。 可以使用 [nslookup set root](nslookup-set-root.md) 命令更改根服务器的名称。

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
