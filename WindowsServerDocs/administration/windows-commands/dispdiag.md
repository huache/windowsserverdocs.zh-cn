---
title: dispdiag
description: Dispdiag 的参考主题，它将显示信息记录到文件中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9f44e261b9c46157fb3e6bb7f9105af2480a60b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719409"
---
# <a name="dispdiag"></a>dispdiag

日志向文件显示信息。

## <a name="syntax"></a>语法

```
dispdiag [-testacpi] [-d] [-delay <Seconds>] [-out <FilePath>]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|- testacpi|运行热键诊断测试。 显示测试期间按下的任何键的键名称、代码和扫描代码。|
|-d|生成包含测试结果的转储文件。|
|-延迟\<秒数>|按指定时间 *（以秒为单位）* 延迟收集数据。|
|-out \<FilePath>|指定用于保存所收集数据的路径和文件名。 这必须是最后一个参数。|
|-?|显示可用的命令参数，并提供使用它们的帮助。|