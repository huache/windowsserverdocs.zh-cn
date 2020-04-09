---
title: manage-bde WipeFreeSpace
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b8d83a2a-c5c8-4019-9041-23d1d6abf282
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6a9995c6872380af61bec5d3b200e733c034ea6b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839710"
---
# <a name="manage-bde-wipefreespace"></a>manage-bde： WipeFreeSpace



擦除卷上的可用空间，删除空间中可能存在的任何数据碎片。 在使用 "仅使用的空间" 加密方法进行加密的卷上运行此命令时，会提供与 "整卷加密" 加密方法相同的保护级别。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
manage-bde -WipeFreeSpace|-w [<Drive>] [-Cancel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<驱动器 >|表示驱动器号后跟冒号、卷 GUID 路径或装入的卷。|
|-Cancel|取消正在进行的擦除可用空间。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<名称 >|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a><a name=BKMK_Examples></a>示例

下面的示例演示如何使用 **-w**命令创建擦除驱动器 C 上的可用空间。
```
manage-bde -w C:
```
下面的示例演示如何使用带有 **-cancel**参数的 **-w**命令取消擦除驱动器 C 上的可用空间。
```
manage-bde -w -Cancel C:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)