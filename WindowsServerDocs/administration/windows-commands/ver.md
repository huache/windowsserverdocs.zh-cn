---
title: ver
description: Ver 的参考文章，其中显示了操作系统的版本号。
ms.topic: reference
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1dcbfc9857d23759f919ad01d98b0436b673206e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636334"
---
# <a name="ver"></a>ver



显示操作系统的版本号。

Windows 命令提示符 ( # A0) ，但在 PowerShell 中不支持此命令。



## <a name="syntax"></a>语法

```
ver
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要从命令 shell 获取操作系统的版本号 ( # A0) ，请键入：

```
ver
```

Ver 命令在 PowerShell 中不起作用。 若要从 PowerShell 获取操作系统版本，请键入：

```powershell
$PSVersionTable.BuildVersion
````


## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
