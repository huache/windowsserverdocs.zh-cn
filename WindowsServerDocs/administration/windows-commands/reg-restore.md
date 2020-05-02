---
title: reg restore
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d490f99f032b38c8bbbe9352b8571b4a85202e1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722524"
---
# <a name="reg-restore"></a>reg restore



将保存的子项和项写入注册表。



## <a name="syntax"></a>语法

```
Reg restore <KeyName> <FileName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName>|指定要还原的子项的完整路径。 还原操作仅适用于本地计算机。 KeyName 必须包含有效的根密钥。 有效的根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。|
|\<文件名>|指定包含要写入注册表的内容的文件的名称和路径。 必须事先使用 **.reg save**操作来创建此文件，并使用 hiv 扩展名。|
|/?|在命令提示符下显示**reg restore**的帮助。|

## <a name="remarks"></a>备注

-   在编辑任何注册表项之前，请用**reg save**操作保存父子项。 如果编辑失败，请将原始子项还原为**reg restore**操作。
-   下表列出了**reg restore**操作的返回值。

|值|描述|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a>示例

若要将名为 NTRKBkUp. hiv 的文件还原到密钥 HKLM\Software\Microsoft\ResKit，并覆盖该项的现有内容，请键入：
```
REG RESTORE HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)