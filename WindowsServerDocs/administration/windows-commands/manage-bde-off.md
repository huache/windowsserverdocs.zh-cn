---
title: manage-bde off
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a27c119-d385-45e5-89fe-e311d4429876
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 588ce453cfca72a029d907be894b142567a43ab5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724146"
---
# <a name="manage-bde-off"></a>manage-bde： off



解密驱动器并关闭 BitLocker。 解密完成后，将删除所有密钥保护程序。

## <a name="syntax"></a>语法

```
manage-bde -off [<Volume>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<卷>|后跟冒号、卷 GUID 路径或已装入卷的驱动器号。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

说明如何使用 **-off**命令在驱动器 C 上关闭 BitLocker。
```
manage-bde –off C:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)