---
title: manage-bde changekey
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 69463db9-7e03-47ff-b233-a95d5055725f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b5f152e4e98387adb7e7780f8458edd409b1a9d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724204"
---
# <a name="manage-bde-changekey"></a>manage-bde： changekey



修改操作系统驱动器的启动密钥。

## <a name="syntax"></a>语法

```
manage-bde -changekey [<Drive>] [<PathToExternalKeyDirectory>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器>|表示驱动器号后跟一个冒号。|
|\<PathToExternalKeyDirectory>|表示要保存可用于解锁驱动器的外部启动密钥文件的目录位置。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

为了说明如何使用 **-changekey**命令在驱动器 E 上创建新的启动密钥，以便在驱动器 C 上与 BitLocker 加密配合使用。
```
manage-bde -changekey C: E:\
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)
