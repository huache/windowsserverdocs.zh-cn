---
title: reg 负载
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3b0b2b1b-f510-4108-9e9d-7057e924aa6e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 140c6b51b9f88081a8686ebebbc9400f241b5ef6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836380"
---
# <a name="reg-load"></a>reg 负载



将保存的子项和项写入注册表中的不同子项。 专用于用于排查或编辑注册表项的临时文件。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
reg load KeyName FileName
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName >|指定要加载的子项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。|
|\<文件名 >|指定要加载的文件的名称和路径。 必须事先使用**reg save**操作和扩展名 hiv 来创建此文件。|
|/?|在命令提示符下显示**reg load**帮助。|

## <a name="remarks"></a>备注

下表列出了**reg load**操作的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将名为 hiv 的文件加载到密钥 HKLM\TempHive，请键入：
```
REG LOAD HKLM\TempHive TempHive.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)