---
title: 让
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55cc7a292b81977a346f3f078a3b5623243ea46c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844800"
---
# <a name="expose"></a>让



将永久性卷影副本作为驱动器号、共享或装入点公开。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|ShadowID|指定要公开的卷影副本的卷影副本 ID。|
|\<驱动器： >|以驱动器号（例如，P：）公开指定的卷影副本。|
|\<共享 >|公开共享中的指定卷影副本（例如 \\\\*MachineName*\)。|
|\<装入点 >|向装入点公开指定的卷影副本（例如，C:\shadowcopy\)。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将与 VSS_SHADOW_1 环境变量关联的持久影子副本作为驱动器 X 公开，请键入：
```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)