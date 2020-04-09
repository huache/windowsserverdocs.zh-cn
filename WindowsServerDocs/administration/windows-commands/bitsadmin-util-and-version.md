---
title: bitsadmin util 和版本
description: 用于显示 BITS 服务版本的 bitsadmin util 和 version 的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 087cc1033166ab93e7496caaa7335433cafd6249
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848830"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util 和版本

显示 BITS 服务的版本（例如，2.0）。

**BITSAdmin 1.5 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /Util /Version [/Verbose]
```

## <a name="remarks"></a>备注

**详细**开关执行以下操作：
-   显示每个与 BITS 相关的 DLL 的文件版本
-   验证是否可以启动 BITS 服务
-   显示位组策略值（仅适用于 Windows Vista）

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例是 BITS 服务的版本。
```
C:\>bitsadmin /Util /Version
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)