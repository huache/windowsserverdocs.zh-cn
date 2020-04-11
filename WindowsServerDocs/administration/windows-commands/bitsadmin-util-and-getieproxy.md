---
title: bitsadmin util 和 getieproxy
description: 适用于**bitsadmin util 和 getieproxy**的 Windows 命令主题，它检索给定服务帐户的代理使用情况。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22b24c4f9c0941c88c70b488a82de47c7901bd8b
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122472"
---
# <a name="bitsadmin-util-and-getieproxy"></a>bitsadmin util 和 getieproxy

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索给定服务帐户的代理使用情况。 此命令显示每个代理使用的值，而不仅仅是为服务帐户指定的代理使用情况。 有关为特定服务帐户设置代理使用情况的详细信息，请参阅[bitsadmin util and setieproxy](bitsadmin-util-and-setieproxy.md)命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /getieproxy <account> [/conn <connectionname>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 帐户 | 指定要检索其代理设置的服务帐户。 可能的值包括：<ul><li>LOCALSYSTEM</li><li>   NETWORKSERVICE</li><li>LOCALSERVICE.</li></ul> |
| connectionname | 可选。 与 **/conn**参数一起使用，以指定要使用的调制解调器连接。 如果未指定 **/conn**参数，则 BITS 将使用 LAN 连接。 |

## <a name="examples"></a>示例

下面的示例显示了网络服务帐户的代理使用情况。

```
C:\>bitsadmin /util /getieproxy NETWORKSERVICE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
