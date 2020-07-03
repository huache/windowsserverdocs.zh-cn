---
title: telnet
description: Telnet 的参考文章，它与运行 telnet 服务器服务的计算机通信。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b70a6156-9413-4300-84ce-a34c467e2b4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a5f588328deb51109ee9139b6e7dfaad8f0166dc
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934225"
---
# <a name="telnet"></a>telnet

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

与运行 telnet 服务器服务的计算机通信。

## <a name="syntax"></a>语法
```
telnet [/a] [/e <EscapeChar>] [/f <FileName>] [/l <UserName>] [/t {vt100 | vt52 | ansi | vtnt}] [<Host> [<Port>]] [/?]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/a|尝试自动登录。 除了使用当前登录的用户的名称外，与/l 选项相同。|
|/e\<EscapeChar>|用于输入 telnet 客户端提示符的转义符。|
|/f \<FileName>|用于客户端日志记录的文件名。|
|/l\<UserName>|指定要在远程计算机上登录的用户名。|
|/t {vt100 &#124; vt52 &#124; ansi &#124; vtnt}|指定终端类型。 支持的终端类型为 vt100、vt52、ansi 和 vtnt。|
|\<Host> [\<Port>]|指定要连接到的远程计算机的主机名或 IP 地址，还可以指定要使用的 TCP 端口（默认为 TCP 端口23）。|
|/?|在命令提示符下显示帮助。 或者，可以键入/h。|

## <a name="remarks"></a>备注
-   必须先安装 telnet 客户端软件，然后才能运行此命令。 有关详细信息，请参阅[安装 telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx)。
-   你可以运行无参数的 telnet，以进入 telnet 上下文，如 telnet 提示符（**Microsoft telnet>**）所示。 在 telnet 提示符下，可以使用 telnet 命令来管理运行 telnet 客户端的计算机。

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
-   [安装 telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx)
-   [telnet 技术参考](https://technet.microsoft.com/library/cc754987(v=ws.10).aspx)
- [命令行语法项](command-line-syntax-key.md)
