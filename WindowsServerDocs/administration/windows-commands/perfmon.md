---
title: perfmon
description: 适用于 perfmon 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a8d5eca-8473-463e-a6e0-7bbd590b18e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/25/2018
ms.openlocfilehash: 7a832416b5b00292a6249f3824644db1b727cfb2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837600"
---
# <a name="perfmon"></a>perfmon

在特定独立模式下启动 Windows 可靠性和性能监视器。

## <a name="syntax"></a>语法

```
perfmon </res|report|rel|sys>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/res|开始资源视图。|
|/report|启动系统诊断数据收集器集，并显示结果报表。|
|/rel|启动可靠性监视器。|
|/sys|启动性能监视器。|

## <a name="additional-references"></a>其他参考

[Windows 性能监视器](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749154(v%3dws.11))
