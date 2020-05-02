---
title: waitfor
description: Waitfor 的参考主题，用于发送或等待系统上的信号。 **Waitfor**用于跨网络同步计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a48ef70d-4d28-4035-b6b0-7d7b46ac2157
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1264fa3bffde303577bd56a0f1f68a6d7b2d98c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720221"
---
# <a name="waitfor"></a>waitfor



发送或等待系统上的信号。 **Waitfor**用于跨网络同步计算机。



## <a name="syntax"></a>语法

```
waitfor [/s <Computer> [/u [<Domain>\]<User> [/p [<Password>]]]] /si <SignalName>
waitfor [/t <Timeout>] <SignalName>
```

### <a name="parameters"></a>参数

|       参数       |                                                                                         描述                                                                                          |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s \<计算机>     | 指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。 此参数适用于命令中指定的所有文件和文件夹。 |
| /u [\<域>\]<User> |                              使用指定用户帐户的凭据运行脚本。 默认情况下， **waitfor**使用当前用户的凭据。                               |
|   /p [\<Password>]    |                                                    指定在 **/u**参数中指定的用户帐户的密码。                                                     |
|          /si          |                                                                        通过网络发送指定的信号。                                                                        |
|     /t \<超时>     |                                              指定等待信号的秒数。 默认情况下， **waitfor**无限期等待。                                               |
|     \<SignalName>     |                                                指定**waitfor**等待或发送的信号。 *SignalName*不区分大小写。                                                 |
|          /?           |                                                                             在命令提示符下显示帮助。                                                                             |

## <a name="remarks"></a>备注

-   信号名称不能超过225个字符。 有效字符包括 a-z、a-z、0-9 和 ASCII 扩展字符集（128-255）。
-   如果不使用 **/s**，则信号会广播到域中的所有系统。 如果使用 **/s**，则信号只发送到指定的系统。
-   您可以在一台计算机上运行多个**waitfor**实例，但每个**waitfor**实例都必须等待不同的信号。 在给定计算机上，只能有一个**waitfor**实例可以等待给定的信号。
-   可以使用 **/si**命令行选项手动激活信号。
-   **Waitfor**只能在运行 windows Server 2003 操作系统的 windows XP 和服务器上运行，但它可以将信号发送到任何运行 windows 操作系统的计算机。
-   如果计算机与发送信号的计算机位于同一域中，则它们只能接收信号。
-   在测试软件生成时，可以使用**waitfor** 。 例如，编译计算机在成功完成编译后，可以将信号发送到运行**waitfor**的几台计算机。 收到信号后，包含**waitfor**的批处理文件可以指示计算机立即开始安装软件或对编译的生成运行测试。

## <a name="examples"></a>示例

若要等到接收到 espresso\build007 信号，请键入：
```
waitfor espresso\build007
```
默认情况下， **waitfor**无限期地等待信号。

若要在超时前等待10秒钟，让 espresso\compile007 收到信号，请键入：
```
waitfor /t 10 espresso\build007
```
若要手动激活 espresso\build007 信号，请键入：
```
waitfor /si espresso\build007
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)