---
title: ver
description: Ver 的参考主题，其中显示了操作系统的版本号。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7050dddda6cc27c50980f2e44f40e1f682c1d375
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720315"
---
# <a name="ver"></a>ver



显示操作系统的版本号。

此命令在 Windows 命令提示符（Cmd.exe）中受支持，但在 PowerShell 中不受支持。



## <a name="syntax"></a>语法

```
ver
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要从命令行界面（cmd.exe）获取操作系统的版本号，请键入：

```
ver
```

Ver 命令在 PowerShell 中不起作用。 若要从 PowerShell 获取操作系统版本，请键入：

```powershell
$PSVersionTable.BuildVersion
````


## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
