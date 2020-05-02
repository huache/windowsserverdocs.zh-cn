---
title: manage-bde WipeFreeSpace
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b8d83a2a-c5c8-4019-9041-23d1d6abf282
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8f1e0f99c226edae467ecb09222b18098ac399ee
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724044"
---
# <a name="manage-bde-wipefreespace"></a>manage-bde： WipeFreeSpace



擦除卷上的可用空间，删除空间中可能存在的任何数据碎片。 在使用 "仅使用的空间" 加密方法进行加密的卷上运行此命令时，会提供与 "整卷加密" 加密方法相同的保护级别。

## <a name="syntax"></a>语法

```
manage-bde -WipeFreeSpace|-w [<Drive>] [-Cancel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器>|表示驱动器号后跟冒号、卷 GUID 路径或装入的卷。|
|-Cancel|取消正在进行的擦除可用空间。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

若要演示如何使用 **-w**命令创建，请擦除驱动器 C 上的可用空间。
```
manage-bde -w C:
```
若要演示如何结合- **w**命令和 **-cancel**参数一起使用来取消擦除驱动器 C 上的可用空间。
```
manage-bde -w -Cancel C:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)