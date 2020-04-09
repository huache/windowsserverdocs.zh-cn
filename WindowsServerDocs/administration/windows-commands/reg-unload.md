---
title: 注册卸载
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1d07791d-ca27-454e-9797-27d7e84c5048
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5fd1436ed1122a09eea11d358a3711aedddf2c1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836270"
---
# <a name="reg-unload"></a>注册卸载



删除使用**reg load**操作加载的注册表部分。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
reg unload <KeyName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<KeyName >|指定要卸载的子项的完整路径。 若要指定远程计算机，请包含计算机名称（格式 \\\\ComputerName\) 作为*KeyName*的一部分。 省略 \\\\ComputerName \ 会使操作默认为本地计算机。 *KeyName*必须包含有效的根密钥。 本地计算机的有效根密钥为 HKLM、HKCU、HKCR、HKU 开头和 HKCC。 如果指定了远程计算机，则有效的根密钥为 HKLM 和 HKU 开头。|
|/?|在命令提示符下显示**reg unload**的帮助。|

## <a name="remarks"></a>备注

下表列出了**reg unload**选项的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要在文件 HKLM 中卸载 hive TempHive，请键入：
```
REG UNLOAD HKLM\TempHive
```

> [!CAUTION]
> 不要直接编辑注册表，除非没有其他方法。 注册表编辑器会绕过标准安全措施，同时允许可能降低性能的设置、损坏系统，甚至要求你重新安装 Windows。 可以通过使用 "控制面板" 或 "Microsoft 管理控制台（MMC）" 中的 "程序" 来安全地更改大多数注册表设置。 如果必须直接编辑注册表，请首先对其进行备份。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)