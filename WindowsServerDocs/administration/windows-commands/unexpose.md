---
title: 隐藏
description: 适用于隐藏的 Windows 命令主题，unexposes 使用 "公开" 命令公开的卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2f8bbdb3b810ffbf9332608a016fc3b3e188e9f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832350"
---
# <a name="unexpose"></a>隐藏

Unexposes 使用**公开**命令公开的卷影副本。 公开的卷影副本可通过其影子 ID、驱动器号、共享或装入点来指定。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ShadowID >|Unexposes 指定的阴影 ID 指定的卷影副本。|
|\<驱动器： >|Unexposes 与指定驱动器号（例如，drive P）关联的卷影副本。|
|\<共享 >|Unexposes 与指定共享关联的卷影副本（例如 \\\\*MachineName*\)。|
|\<装入点 >|Unexposes 与指定装入点（例如，C:\shadowcopy\)关联的卷影副本。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要隐藏与 Drive P 关联的卷影副本，请键入：
```
unexpose P:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)