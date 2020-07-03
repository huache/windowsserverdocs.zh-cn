---
title: ver
description: Ver 的参考文章，其中显示了操作系统的版本号。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd9b40fa526c2917b6cdcbc8d54da510eb40bc53
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931342"
---
# <a name="ver"></a>ver



显示操作系统的版本号。

此命令在 Windows 命令提示符（Cmd.exe）中受支持，但在 PowerShell 中不受支持。



## <a name="syntax"></a>语法

```
ver
```

### <a name="parameters"></a>参数

|参数|说明|
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
