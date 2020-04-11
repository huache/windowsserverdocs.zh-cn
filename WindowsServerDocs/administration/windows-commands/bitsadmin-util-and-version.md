---
title: bitsadmin util 和版本
description: 用于显示 BITS 服务版本的**bitsadmin util 和 version**的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c2518eb7a8f15d9a592ed9a77dd67a6f8d8afac
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122471"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util 和版本

显示 BITS 服务的版本（例如，2.0）。

> [!NOTE]
> BITS 1.5 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /version [/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /verbose | 使用此开关可以显示每个与 BITS 相关的 DLL 的文件版本，并验证 BITS 服务是否可以启动。|

## <a name="examples"></a>示例

下面的示例是 BITS 服务的版本。

```
C:\>bitsadmin /util /version
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)