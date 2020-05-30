---
title: lpq
description: Lpq 命令的参考主题，该命令显示运行 Line printer Daemon （LPD）的计算机上打印队列的状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ecce9b1b4255e5e769fe76b0f753226d61fa916
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222730"
---
# <a name="lpq"></a>lpq

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示运行 Line printer Daemon （LPD）的计算机上打印队列的状态。

## <a name="syntax"></a>语法

```
lpq -S <servername> -P <printername> [-l]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -S`<servername>` | 使用要显示的状态指定（按名称或 IP 地址）承载 LPD 打印队列的计算机或打印机共享设备。 此参数是必需的，必须大写。 |
| -P`<Printername>` | 用要显示的状态指定（按名称）打印队列的打印机。 此参数是必需的，必须大写。 |
| -l | 指定您希望显示有关打印队列状态的详细信息。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要在*10.0.0.45*上显示 LPD 主机上的*Laserprinter1*打印机队列的状态，请键入：

```
lpq -S 10.0.0.45 -P Laserprinter1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
