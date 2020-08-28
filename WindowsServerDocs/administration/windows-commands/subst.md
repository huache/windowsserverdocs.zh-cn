---
title: subst
description: 了解如何将路径与驱动器号关联。
ms.topic: reference
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 680a3118d284d18946980ff8dc246ce08b5ea727
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024611"
---
# <a name="subst"></a>subst



将路径与驱动器号关联。 如果在没有参数的情况下使用，则 **subst** 显示有效虚拟驱动器的名称。



## <a name="syntax"></a>语法

```
subst [<Drive1>: [<Drive2>:]<Path>]
subst <Drive1>: /d
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<Drive1>:|指定要为其分配路径的虚拟驱动器。|
|[\<Drive2>:]\<Path>|指定要分配给虚拟驱动器的物理驱动器和路径。|
|/d|删除替换 (虚拟) 驱动器。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>注解

-   以下命令不起作用，不应在 **subst** 命令中指定的驱动器上使用：

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   *Drive1*参数必须在**lastdrive**命令指定的范围内。 否则， **subst** 会显示以下错误消息：

    `Invalid parameter - drive1:`

## <a name="examples"></a><a name="BKMK_examples"></a>示例

若要为路径 B:\User\Betty\Forms 创建虚拟驱动器 Z，请键入：
```
subst z: b:\user\betty\forms
```
不要键入完整路径，而是通过键入虚拟驱动器的字母并在后面加上冒号，来访问此目录：
```
z:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)