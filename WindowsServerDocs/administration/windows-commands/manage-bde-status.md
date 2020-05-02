---
title: manage-bde 状态
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1444a360-fabf-4dd3-b67f-188e6ea3fa5b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d1bf42da356d8326f459066fc168bbd38b7765b0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724079"
---
# <a name="manage-bde-status"></a>manage-bde：状态



提供有关计算机上所有驱动器的下列信息：是否受 BitLocker 保护：
-   大小
-   BitLocker 版本
-   转换状态
-   加密百分比
-   加密方法
-   保护状态
-   锁定状态
-   标识字段
-   密钥保护程序



## <a name="syntax"></a>语法

```
manage-bde -status [<Drive>] [-protectionaserrorlevel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<驱动器>|表示驱动器号后跟一个冒号。|
|-protectionaserrorlevel|使 manage-bde 命令行工具在卷受保护时发送返回代码0，并在卷未受保护时返回 1;最常见的批处理脚本用于确定驱动器是否受 BitLocker 保护。 你还可以使用 **-p**作为此命令的缩写形式。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

说明如何使用 **-status**命令显示驱动器 C 的状态。
```
manage-bde –status C:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)