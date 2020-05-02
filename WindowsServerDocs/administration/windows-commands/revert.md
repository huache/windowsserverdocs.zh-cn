---
title: 回到
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b967904c28661be82909ebcc0aa7cb42c73e418c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722326"
---
# <a name="revert"></a>回到



将卷恢复到指定的卷影副本。 仅在 CLIENTACCESSIBLE 上下文中对卷影副本支持此项。 这些卷影副本是持久的，只能由系统提供程序进行。 如果不使用参数，则**revert**会在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
revert <ShadowCopyID>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<ShadowCopyID>|指定卷的卷影副本 ID。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)