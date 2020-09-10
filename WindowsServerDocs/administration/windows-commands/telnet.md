---
title: telnet
description: Telnet 的参考文章，它与运行 telnet 服务器服务的计算机通信。
ms.topic: reference
ms.assetid: b70a6156-9413-4300-84ce-a34c467e2b4e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9110bd2f3d4c701e46c8a52af48773f7d5a1026b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640806"
---
# <a name="telnet"></a>telnet

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

与运行 telnet 服务器服务的计算机通信。

## <a name="syntax"></a>语法
```
telnet [/a] [/e <EscapeChar>] [/f <FileName>] [/l <UserName>] [/t {vt100 | vt52 | ansi | vtnt}] [<Host> [<Port>]] [/?]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/a|尝试自动登录。 除了使用当前登录的用户的名称外，与/l 选项相同。|
|/e \<EscapeChar>|用于输入 telnet 客户端提示符的转义符。|
|/f \<FileName>|用于客户端日志记录的文件名。|
|/l \<UserName>|指定要在远程计算机上登录的用户名。|
|/t {vt100 &#124; vt52 &#124; ansi &#124; vtnt}|指定终端类型。 支持的终端类型为 vt100、vt52、ansi 和 vtnt。|
|\<Host> [\<Port>]|指定要连接到的远程计算机的主机名或 IP 地址，还可以选择要使用的 TCP 端口 (默认为 TCP 端口 23) 。|
|/?|在命令提示符下显示帮助。 或者，可以键入/h。|

## <a name="remarks"></a>备注
-   必须先安装 telnet 客户端软件，然后才能运行此命令。 有关详细信息，请参阅 [安装 telnet](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293(v=ws.10))。
-   您可以运行无参数的 telnet，以进入 telnet 上下文，由 telnet 提示符指示 (**Microsoft telnet>**) 。 在 telnet 提示符下，可以使用 telnet 命令来管理运行 telnet 客户端的计算机。

## <a name="examples"></a>示例
使用 telnet 连接到运行 telnet 服务器服务的计算机，网址为 telnet.microsoft.com。
```
telnet telnet.microsoft.com
```
使用 telnet 连接到在 TCP 端口44上的 telnet.microsoft.com 中运行 telnet 服务器服务的计算机，并在名为 telnetlog.txt 的本地文件中记录会话活动。
```
telnet /f telnetlog.txt telnet.microsoft.com 44
```

## <a name="additional-references"></a>其他参考
-   [安装 telnet](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293(v=ws.10))
-   [telnet 技术参考](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754987(v=ws.10))
- [命令行语法项](command-line-syntax-key.md)
