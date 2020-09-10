---
title: lpq
description: Lpq 命令的参考文章，其中显示了运行 Line printer Daemon (LPD) 的计算机上打印队列的状态。
ms.topic: reference
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f112216f2692f1bef5156566c39431f4ecebc7a8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636573"
---
# <a name="lpq"></a>lpq

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示运行 Line printer Daemon (LPD) 的计算机上打印队列的状态。

## <a name="syntax"></a>语法

```
lpq -S <servername> -P <printername> [-l]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -S `<servername>` | 按名称或 IP 地址指定 () 使用要显示的状态承载 LPD 打印队列的计算机或打印机共享设备。 此参数是必需的，必须大写。 |
| -P `<Printername>` | 按名称指定 () 要显示其状态的打印队列的打印机。 此参数是必需的，必须大写。 |
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
