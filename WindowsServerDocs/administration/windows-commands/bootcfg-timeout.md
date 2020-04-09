---
title: bootcfg timeout
description: 适用于 bootcfg timeout 的 Windows 命令主题，它更改操作系统超时值。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b56e609d5e3b7c92a887a98ae5d02bfbfb7a78e6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848490"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改操作系统超时值。

## <a name="syntax"></a>语法

```
bootcfg /timeout <timeOutValue> [/s <computer> [/u <Domain\User>/p <Password>]]
```

### <a name="parameters"></a>参数


|        参数        |                                                                                                                                                                                  说明                                                                                                                                                                                   |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /timeout <timeOutValue> | 指定 [boot loader] 部分中的超时值。 <timeOutValue> 是用户在 NTLDR 加载默认值之前必须从启动加载器屏幕中选择操作系统的秒数。 <timeOutValue> 的有效范围是0-999。 如果该值为0，则 NTLDR 会立即启动默认操作系统，而不显示启动加载程序屏幕。 |
|      /s <computer>      |                                                                                                                               指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                                                                                                               |
|    /u < Domain\User >     |                                                                                       使用 <User> 或 < Domain\User > 指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。                                                                                        |
|      /p <Password>      |                                                                                                                                            指定在 **/u**参数中指定的用户帐户的 <Password>。                                                                                                                                             |
|           /?            |                                                                                                                                                                      在命令提示符下显示帮助。                                                                                                                                                                      |

## <a name="examples"></a><a name=BKMK_examples></a>示例
下面的示例演示如何使用**bootcfg/timeout**命令：
```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
