---
title: 回到
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7dae609e4615868b03e4b5ea9a681f553aa0667
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835750"
---
# <a name="revert"></a>回到



将卷恢复到指定的卷影副本。 仅在 CLIENTACCESSIBLE 上下文中对卷影副本支持此项。 这些卷影副本是持久的，只能由系统提供程序进行。 如果不使用参数，则**revert**会在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
revert <ShadowCopyID>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ShadowCopyID >|指定卷的卷影副本 ID。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)