---
title: reg restore
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e511694247c04f2befc9c0148498e43b85f664ed
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836360"
---
# <a name="reg-restore"></a>reg restore



将保存的子项和项写入注册表。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
Reg restore <KeyName> <FileName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName >|指定要还原的子项的完整路径。 还原操作仅适用于本地计算机。 KeyName 必须包含有效的根密钥。 有效的根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。|
|\<文件名 >|指定包含要写入注册表的内容的文件的名称和路径。 必须事先使用 **.reg save**操作来创建此文件，并使用 hiv 扩展名。|
|/?|在命令提示符下显示**reg restore**的帮助。|

## <a name="remarks"></a>备注

-   在编辑任何注册表项之前，请用**reg save**操作保存父子项。 如果编辑失败，请将原始子项还原为**reg restore**操作。
-   下表列出了**reg restore**操作的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将名为 NTRKBkUp. hiv 的文件还原到密钥 HKLM\Software\Microsoft\ResKit，并覆盖该项的现有内容，请键入：
```
REG RESTORE HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)