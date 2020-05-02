---
title: bitsadmin util 和 getieproxy
description: Bitsadmin util 和 getieproxy 命令的参考主题，它检索给定服务帐户的代理使用情况。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 576f308bc7fb9a4e448638d06621f95eebef0cd0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707664"
---
# <a name="bitsadmin-util-and-getieproxy"></a>bitsadmin util 和 getieproxy

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索给定服务帐户的代理使用情况。 此命令显示每个代理使用的值，而不仅仅是为服务帐户指定的代理使用情况。 有关为特定服务帐户设置代理使用情况的详细信息，请参阅[bitsadmin util and setieproxy](bitsadmin-util-and-setieproxy.md)命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /getieproxy <account> [/conn <connectionname>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ---------- |
| account | 指定要检索其代理设置的服务帐户。 可能的值包括：<ul><li>LOCALSYSTEM</li><li>   NETWORKSERVICE</li><li>LOCALSERVICE.</li></ul> |
| connectionname | 可选。 与 **/conn**参数一起使用，以指定要使用的调制解调器连接。 如果未指定 **/conn**参数，则 BITS 将使用 LAN 连接。 |

## <a name="examples"></a>示例

显示网络服务帐户的代理用法：

```
bitsadmin /util /getieproxy NETWORKSERVICE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin util 命令](bitsadmin-util.md)

- [bitsadmin 命令](bitsadmin.md)
