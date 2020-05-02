---
title: nfsstat
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da7a9768-44bd-404b-97ee-c388d00dc395
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e2c02fdfeb9923993a1d4471862a6c8487c9d86
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723756"
---
# <a name="nfsstat"></a>nfsstat



你可以使用**nfsstat**来显示或重置对 NFS 服务器的调用计数。

## <a name="syntax"></a>语法

```
nfsstat [-z]
```

## <a name="description"></a>说明

当未使用 **-z**选项时， **nfsstat**命令行实用工具将显示对服务器所做的 NFS V2、Nfs v3 和 Mount V3 调用数，因为计数器设置为0（在服务启动时或者计数器使用**nfsstat**重置时）。