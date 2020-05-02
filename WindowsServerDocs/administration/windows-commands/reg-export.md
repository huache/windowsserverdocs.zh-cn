---
title: reg export
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2c697595d5d19c953ef85f7a2e334c6fe05329d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722565"
---
# <a name="reg-export"></a>reg export



将本地计算机的指定子项、项和值复制到文件中，以便传输到其他服务器。



## <a name="syntax"></a>语法

```
Reg export KeyName FileName [/y]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName>|指定子项的完整路径。 导出操作仅适用于本地计算机。 KeyName 必须包含有效的根密钥。 有效的根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。|
|\<文件名>|指定要在操作过程中创建的文件的名称和路径。 文件必须具有 .reg 扩展名。|
|/y|用名称*文件名*覆盖任何现有文件，并且不提示确认。|
|/?|在命令提示符下显示**reg export**的帮助。|

## <a name="remarks"></a>备注

下表列出了**reg 导出**操作的返回值。

|值|描述|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a>示例

若要将项 MyApp 的所有子项和值的内容导出到文件 AppBkUp，请键入：
```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)