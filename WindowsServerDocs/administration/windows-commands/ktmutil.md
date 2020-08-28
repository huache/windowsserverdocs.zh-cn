---
title: ktmutil
description: 用于启动内核事务管理器实用工具的 ktmutil 命令的参考文章。
ms.topic: reference
ms.assetid: 53bc56df-f0e5-443b-ab20-bbf8b11d4a9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2bc69964d0fbf7ad93a91b16f78ed86515e537b3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028255"
---
# <a name="ktmutil"></a>ktmutil

启动内核事务管理器实用工具。 如果不使用参数，则 **ktmutil** 显示可用的子命令。

## <a name="syntax"></a>语法

```
ktmutil list tms
ktmutil list transactions [{TmGUID}]
ktmutil resolve complete {TmGUID} {RmGUID} {EnGUID}
ktmutil resolve commit {TxGUID}
ktmutil resolve rollback {TxGUID}
ktmutil force commit {GUID}
ktmutil force rollback {GUID}
ktmutil forget
```

## <a name="examples"></a>示例


若要强制提交 GUID 为311a9209-03f4-11dc-918f-00188b8f707b 的 Indoubt 事务，请键入：

```
ktmutil force commit {311a9209-03f4-11dc-918f-00188b8f707b}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)