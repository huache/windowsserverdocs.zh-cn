---
title: ktmutil
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 53bc56df-f0e5-443b-ab20-bbf8b11d4a9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47b447165ee54e6839bb6338801c6703d818caa8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724526"
---
# <a name="ktmutil"></a>ktmutil



启动内核事务管理器实用工具。 如果不使用参数，则**ktmutil**显示可用的子命令。



## <a name="syntax"></a>语法

```
ktmutil list tms 
ktmutil list transactions [{TmGuid}]
ktmutil resolve complete {TmGuid} {RmGuid} {EnGuid}
ktmutil resolve commit {TxGuid}
ktmutil resolve rollback {TxGuid}
ktmutil force commit {??Guid}
ktmutil force rollback {??Guid}
ktmutil forget
```

### <a name="parameters"></a>参数

## <a name="remarks"></a>备注

## <a name="examples"></a>示例

若要强制提交 GUID 为311a9209-03f4-11dc-918f-00188b8f707b 的 Indoubt 事务，请键入：
```
ktmutil force commit {311a9209-03f4-11dc-918f-00188b8f707b}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)