---
title: subst
description: 了解如何将路径与驱动器号关联。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 62ba0de33e69998e7d3e343b1e53c1de7e630e10
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721613"
---
# <a name="subst"></a>subst



将路径与驱动器号关联。 如果在没有参数的情况下使用，则**subst**显示有效虚拟驱动器的名称。



## <a name="syntax"></a>语法

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<Drive1>：|指定要为其分配路径的虚拟驱动器。|
|[\<Drive2>：]\<路径>|指定要分配给虚拟驱动器的物理驱动器和路径。|
|/d|删除替代的（虚拟）驱动器。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   以下命令不起作用，不应在**subst**命令中指定的驱动器上使用：

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   *Drive1*参数必须在**lastdrive**命令指定的范围内。 否则， **subst**会显示以下错误消息：

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