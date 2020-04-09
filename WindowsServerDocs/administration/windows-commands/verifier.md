---
title: verifier
description: 验证程序的 Windows 命令主题，它运行驱动程序验证程序管理器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f0f4c35e732f520076df9ec89b9417c744d5c44
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830170"
---
# <a name="verifier"></a>verifier

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

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
|\<标志 >|必须是十进制或十六进制，位数的组合：<p>-   **值：说明**<br />-   **位0：** 特殊池检查<br />-   **位1：** 强制 irql 检查<br />-   **位2：** 低资源模拟<br />-   **位3：** 池跟踪<br />-   **位4：** i/o 验证<br />-   **位5：** 死锁检测<br />-   **位6：** 未使用<br />-   **位7：** DMA 验证<br />-   **位8：** 安全检查<br />-   **位9：** 强制挂起的 i/o 请求<br />-   **位10：** IRP 日志记录<br />-   **位11：** 其他检查<p>例如， **/flags 27**等效于 **/flags 0x1b**|  
|/volatile|用于动态更改验证程序设置，而无需重新启动系统。 系统重新启动后，任何新的设置都将丢失。|  
|\<概率 >|1到10000之间的数字，用于指定错误注入概率。 例如，指定100表示错误注入概率为1% （100/10000）。<p>如果未指定此参数，则将使用默认概率6%。|  
|\<标记 >|指定将使用错误分隔的池标记，由空格分隔。 如果未指定此参数，则可以注入具有错误的任何池分配。|  
|\<应用程序 >|指定将注入错误的应用程序的图像文件名，用空格分隔。 如果未指定此参数，则在任何应用程序中都可以进行低资源模拟。|  
|\<分钟 >|一个正数，指定重新启动后的时间长度（以分钟为单位），在此期间不会发生错误注入。 如果未指定此参数，则将使用默认长度8分钟。|  
|/?|在命令提示符下显示帮助。|  

## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  