---
title: 隐藏
description: 隐藏的参考主题，它 unexposes 使用公开命令公开的卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e0caa412e5ff7de149f0a2bd8806f7141c368306
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721186"
---
# <a name="unexpose"></a>隐藏

Unexposes 使用**公开**命令公开的卷影副本。 公开的卷影副本可通过其影子 ID、驱动器号、共享或装入点来指定。



## <a name="syntax"></a>语法

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<ShadowID>|Unexposes 指定的阴影 ID 指定的卷影副本。|
|\<驱动器： >|Unexposes 与指定驱动器号（例如，drive P）关联的卷影副本。|
|\<共享>|Unexposes 与指定共享关联的卷影副本（例如， \\ \\*计算机名*\)。|
|\<装入点>|Unexposes 与指定装入点关联的卷影副本（例如，C:\shadowcopy\)。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a>示例

若要隐藏与 Drive P 关联的卷影副本，请键入：
```
unexpose P:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)