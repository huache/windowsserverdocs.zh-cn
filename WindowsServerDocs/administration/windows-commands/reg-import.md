---
title: 注册导入
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e7e033091752f97086fd27fcb94e62469f0cced
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722554"
---
# <a name="reg-import"></a>注册导入



将包含导出的注册表子项、项和值的文件的内容复制到本地计算机的注册表中。



## <a name="syntax"></a>语法

```
Reg import FileName
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<文件名>|指定包含要复制到本地计算机的注册表中的内容的文件的名称和路径。 必须使用**reg export**提前创建此文件。|
|/?|在命令提示符下显示**reg import**的帮助。|

## <a name="remarks"></a>备注

下表列出了**reg import**操作的返回值。

|值|描述|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a>示例

若要从名为 AppBkUp 的文件中导入注册表项，请键入：
```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)