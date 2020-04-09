---
title: 注册保存
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b326482b-c8af-467d-a20c-0481eeda3d5c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b1f7829aedc42c0b75bda951572a4c944798ec6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836350"
---
# <a name="reg-save"></a>注册保存



在指定的文件中保存指定子项、项和注册表值的副本。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
reg save <KeyName> <FileName> [/y]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName >|指定子项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。|
|\<文件名 >|指定创建的文件的名称和路径。 如果未指定路径，则使用当前路径。|
|/y|使用名称*文件名*覆盖现有文件，而不提示确认。|
|/?|在命令提示符下显示**reg save**的帮助。|

## <a name="remarks-optional-section"></a>备注 \<可选部分 >

-   下表列出了**reg save**操作的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|
-   在编辑任何注册表项之前，请用**reg save**操作保存父子项。 如果编辑失败，请将原始子项还原为**reg restore**操作。

## <a name="examples"></a><a name=BKMK_examples></a>示例

要将 hive MyApp 保存到当前文件夹中作为名为 AppBkUp 的文件，请键入：
```
REG SAVE HKLM\Software\MyCo\MyApp AppBkUp.hiv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)