---
title: “选择设备” 列表
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57b6c8d0-872e-4dba-9715-1db8ab892e98
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d60c42b868a1e9a26e3168e4b489573f9f87e179
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841100"
---
# <a name="list"></a>“选择设备” 列表



列出系统上的编写器、卷影副本或当前注册的卷影复制提供程序。 如果在没有参数的情况下使用，则**列表**将在命令提示符下显示帮助。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
list writers [metadata | detailed | status]
list shadows {all | set <SetID> | id <ShadowID>}
list providers
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|写入器|列出编写器。 请参阅列出语法和参数的[编写](list-writers.md)器。|
|影|列出持久的和现有的非持久影副本。 有关语法和参数，请参阅[列出阴影](list-shadows.md)。|
|提供程序|列出当前已注册的卷影复制提供程序。 请参阅[列出提供程序](list-providers.md)的语法和参数。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要列出所有卷影副本，请键入：
```
list shadows all
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)