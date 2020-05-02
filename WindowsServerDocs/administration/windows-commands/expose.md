---
title: 让
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 500dc5cfcd5e2bba4cfbc3cb5ef81a9065ea53cf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725671"
---
# <a name="expose"></a>让



将永久性卷影副本作为驱动器号、共享或装入点公开。



## <a name="syntax"></a>语法

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|ShadowID|指定要公开的卷影副本的卷影副本 ID。|
|\<驱动器： >|以驱动器号（例如，P：）公开指定的卷影副本。|
|\<共享>|公开共享中的指定卷影副本（例如， \\ \\*计算机名*\)。|
|\<装入点>|向装入点公开指定的卷影副本（例如，C:\shadowcopy\)。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a>示例

若要将与 VSS_SHADOW_1 环境变量关联的持久影子副本作为驱动器 X 公开，请键入：
```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)