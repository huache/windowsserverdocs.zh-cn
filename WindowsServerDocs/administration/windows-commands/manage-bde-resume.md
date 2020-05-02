---
title: manage-bde 恢复
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ca3cd1ca-6f2c-4190-b68f-27816635facb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ecd5900dba2cb4ed7f7a3d4e2a2924a3393e94b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724106"
---
# <a name="manage-bde-resume"></a>manage-bde： resume



在暂停后恢复 BitLocker 加密或解密。

## <a name="syntax"></a>语法

```
manage-bde -resume [<Drive>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器>|表示驱动器号后跟一个冒号。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

说明如何使用 **-resume**命令在驱动器 C 上恢复 BitLocker 加密。
```
manage-bde –resume C:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)