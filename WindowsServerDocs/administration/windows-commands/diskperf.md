---
title: diskperf
description: 适用于 diskperf 的 Windows 命令主题，可用于在运行 Windows 2000 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b07471c051d57d0279e4fd8b38afdc4acdc4069
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845460"
---
# <a name="diskperf"></a>diskperf

在 Windows 2000 中，默认情况下不启用物理磁盘和逻辑磁盘性能计数器。

**Diskperf**包含在 windows XP、windows server 2003、windows server 2008、windows Vista、windows Server 2008 R2 和 windows 7 中，因此可用于在运行 Windows 2000 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。

## <a name="syntax"></a>语法

```
diskperf [-Y[D|V] | -N[D|V]] [\\computername]
```

## <a name="options"></a>Options

|选项|说明|
|------|-----------|
|-?|显示上下文相关的帮助。|
|-Y|计算机重新启动时，启动所有磁盘性能计数器。|
|-YD|计算机重新启动时，为物理驱动器启用磁盘性能计数器。|
|-YV|计算机重新启动时，为逻辑驱动器或存储卷启用磁盘性能计数器。|
|-N|在计算机重新启动时禁用所有磁盘性能计数器。|
|-ND|计算机重新启动时，禁用物理驱动器的磁盘性能计数器。|
|-NV|计算机重新启动时，禁用逻辑驱动器或存储卷的磁盘性能计数器。|
|\\\\ *\<computername >*|指定要在其中启用或禁用磁盘性能计数器的计算机的名称。|