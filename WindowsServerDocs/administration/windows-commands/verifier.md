---
title: verifier
description: 验证程序的参考文章，其中运行了驱动程序验证程序管理器。
ms.topic: reference
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1cdad5521d4ed6eb5b31bcbed9d09fd662200f71
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636323"
---
# <a name="verifier"></a>verifier

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

驱动程序验证程序管理器。

## <a name="syntax"></a>语法
```
verifier /standard /driver <name> [<name> ...]
verifier /standard /all
verifier [/flags <flags>] [/faults [<probability> [<tags> [<applications> [<minutes>]]]] /driver <name> [<name>...]
verifier [/flags FLAGS] [/faults [<probability> [<tags> [<applications> [<minutes>]]]] /all
verifier /querysettings
verifier /volatile /flags <flags>
verifier /volatile /adddriver <name> [<name>...]
verifier /volatile /removedriver <name> [<name>...]
verifier /volatile /faults [<probability> [<tags> [<applications>]]
verifier /reset
verifier /query
verifier /log <LogFileName> [/interval <seconds>]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|\<flags>|必须是十进制或十六进制，位数的组合：<p>-   **值：说明**<br />-   **位0：** 特殊池检查<br />-   **第1位：** 强制 irql 检查<br />-   **第2位：** 低资源模拟<br />-   **位3：** 池跟踪<br />-   **位4：** I/o 验证<br />-   **位5：** 死锁检测<br />-   **位6：** 未使用<br />-   **第7位：** DMA 验证<br />-   **位8：** 安全检查<br />-   第**9 位：** 强制挂起 i/o 请求<br />-   **位10：** IRP 日志记录<br />-   **位11：** 其他检查<p>例如， **/flags 27** 等效于 **/flags 0x1b**|
|/volatile|用于动态更改验证程序设置，而无需重新启动系统。 系统重新启动后，任何新的设置都将丢失。|
|\<probability>|1到10000之间的数字，用于指定错误注入概率。 例如，指定100表示错误注入概率为 1% (100/10000) 。<p>如果未指定此参数，则将使用默认概率6%。|
|\<tags>|指定将使用错误分隔的池标记，由空格分隔。 如果未指定此参数，则可以注入具有错误的任何池分配。|
|\<applications>|指定将注入错误的应用程序的图像文件名，用空格分隔。 如果未指定此参数，则在任何应用程序中都可以进行低资源模拟。|
|\<minutes>|一个正数，指定重新启动后的时间长度（以分钟为单位），在此期间不会发生错误注入。 如果未指定此参数，则将使用默认长度8分钟。|
|/?|在命令提示符下显示帮助。|

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)