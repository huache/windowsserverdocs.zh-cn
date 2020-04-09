---
title: 注册删除
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cee05071-1607-4ab1-b8ab-65caebeb85c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 726a3c700a9278dbc7abb1873aae7ea3c957bbb5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836500"
---
# <a name="reg-delete"></a>注册删除



删除注册表中的一个或一些项。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
Reg delete <KeyName> [{/v ValueName | /ve | /va}] [/f]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName >|指定要删除的子项或项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为： HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为： HKLM 和 HKU 开头。|
|/v \<ValueName >|删除子项下的特定项。 如果未指定任何项，则将删除子项下的所有项和子项。|
|/ve|指定仅删除没有值的条目。|
|/va|删除指定子项下的所有条目。 不会删除指定子项下的子项。|
|/f|删除现有的注册表子项或条目，而不要求确认。|
|/?|在命令提示符下显示**reg delete**的帮助。|

## <a name="remarks"></a>备注

下表列出了**reg delete**操作的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要删除注册表项超时及其所有子项和值，请键入：
```
REG DELETE HKLM\Software\MyCo\MyApp\Timeout
```
若要在名为天干地支的计算机上的 HKLM\Software\MyCo 下删除注册表值 MTU，请键入：
```
REG DELETE \\ZODIAC\HKLM\Software\MyCo /v MTU
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)