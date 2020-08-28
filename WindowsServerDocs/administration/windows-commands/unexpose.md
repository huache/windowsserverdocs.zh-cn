---
title: unexpose
description: 隐藏的参考文章，其中 unexposes 了使用公开命令公开的卷影副本。
ms.topic: reference
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 13e14941e2c67aa0361dcc0af2cdb1a36bf7e651
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036405"
---
# <a name="unexpose"></a>unexpose

Unexposes 使用 **公开** 命令公开的卷影副本。 公开的卷影副本可通过其影子 ID、驱动器号、共享或装入点来指定。



## <a name="syntax"></a>语法

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ShadowID>|Unexposes 指定的阴影 ID 指定的卷影副本。|
|\<Drive:>|Unexposes 与指定驱动器号关联的卷影副本 (例如，drive P) 。|
|\<Share>|Unexposes 与指定共享关联的卷影副本 (例如， \\ \\ *计算机名* \) 。|
|\<MountPoint>|Unexposes 与指定装入点关联的卷影副本 (例如，C:\shadowcopy \) 。|

## <a name="remarks"></a>注解

-   您可以使用现有的别名或环境变量来代替 *ShadowID*。 使用 **add** 而不使用参数查看现有别名。

## <a name="examples"></a>示例

若要隐藏与 Drive P 关联的卷影副本，请键入：
```
unexpose P:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)