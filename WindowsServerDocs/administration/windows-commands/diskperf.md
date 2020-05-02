---
title: diskperf
description: Diskperf 的参考主题，可用于在运行 Windows 2000 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c8f505d924ee1de311f2f2736ff65be844c3f2ea
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719449"
---
# <a name="diskperf"></a>diskperf

在 Windows 2000 中，默认情况下不启用物理磁盘和逻辑磁盘性能计数器。

**Diskperf**包含在 windows XP、windows server 2003、windows server 2008、windows Vista、windows Server 2008 R2 和 windows 7 中，因此可用于在运行 Windows 2000 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。

## <a name="syntax"></a>语法

```
diskperf [-Y[D|V] | -N[D|V]] [\\computername]
```

## <a name="options"></a>选项

|选项|描述|
|------|-----------|
|-?|显示上下文相关的帮助。|
|-y|计算机重新启动时，启动所有磁盘性能计数器。|
|-YD|计算机重新启动时，为物理驱动器启用磁盘性能计数器。|
|-YV|计算机重新启动时，为逻辑驱动器或存储卷启用磁盘性能计数器。|
|-N|在计算机重新启动时禁用所有磁盘性能计数器。|
|-ND|计算机重新启动时，禁用物理驱动器的磁盘性能计数器。|
|-NV|计算机重新启动时，禁用逻辑驱动器或存储卷的磁盘性能计数器。|
|\\\\*\<computername>*|指定要在其中启用或禁用磁盘性能计数器的计算机的名称。|