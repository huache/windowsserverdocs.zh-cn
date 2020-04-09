---
title: 设置上下文
description: 设置上下文的 Windows 命令主题，用于设置创建卷影副本的上下文。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc16c7dd-e8f0-4c2a-8742-0bddb2848bfd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 162fefc46bc3b8ae39dcb41a387e50ed98fefa70
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834560"
---
# <a name="set-contex"></a>设置上下文

设置用于创建卷影副本的上下文。 如果使用时没有参数，则**设置上下文将**在命令提示符下显示帮助。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|clientaccessible|指定卷影副本可供 Windows 的客户端版本使用。|
|式|指定卷影副本在程序退出、重置或重新启动时保持不变。|
|volatile|退出或重置时删除卷影副本。|
|nowriters|指定排除所有编写器。|

## <a name="remarks"></a>备注

-   默认情况下， *clientaccessible*上下文是永久性的。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要防止在退出 DiskShadow 时删除卷影副本，请键入：
```
set context persistent
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)