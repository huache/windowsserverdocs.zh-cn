---
title: ftp
description: Ftp 命令的参考主题，用于在运行文件传输协议（ftp）服务器服务的计算机之间传输文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 758335e1-fd8d-448c-a654-993126239dd9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3920306ce05aeb1b1e364c8146c461ea187f6560
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820237"
---
# <a name="ftp"></a>ftp

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在运行文件传输协议（ftp）服务器服务的计算机之间传输文件。 可以通过交互方式或以批处理模式使用此命令，方法是处理 ASCII 文本文件。

## <a name="syntax"></a>语法

```
ftp [-v] [-d] [-i] [-n] [-g] [-s:<filename>] [-a] [-A] [-x:<sendbuffer>] [-r:<recvbuffer>] [-b:<asyncbuffers>][-w:<windowssize>][<host>] [-?]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ----------| ----------- |
| -v | 禁止显示远程服务器响应。 |
| -d | 启用调试，并显示在 FTP 客户端和 FTP 服务器之间传递的所有命令。 |
| -i | 在多个文件传输过程中禁用交互式提示。 |
| -n | 在初始连接时禁止自动登录。 |
| -g | 禁用文件名组合。  **Glob**允许将星号（*）和问号（？）用作本地文件和路径名称中的通配符字符。 |
| 些`<filename>` | 指定包含**ftp**命令的文本文件。 这些命令将在**ftp**启动后自动运行。 此参数不允许有空格。 使用此参数，而不是重定向（ `<` ）。 **注意：** 在 Windows 8 和 Windows Server 2012 或更高版本的操作系统中，必须用 UTF-8 编写文本文件。 |
| -a | 指定在绑定 ftp 数据连接时可以使用任何本地接口。 |
| -A | 以匿名方式登录到 ftp 服务器。 |
| x-blade`<sendbuffer> `| 覆盖默认 SO_SNDBUF 大小为8192。 |
| 迅驰`<recvbuffer>` | 覆盖默认 SO_RCVBUF 大小为8192。 |
| b`<asyncbuffers>` | 替代的默认异步缓冲区计数为3。 |
| 水平`<windowssize>` | 指定传输缓冲区的大小。 默认窗口大小为4096个字节。 |
| `<host>` | 指定要连接的 ftp 服务器的计算机名称、IP 地址或 IPv6 地址。 如果指定，主机名或地址必须是行中的最后一个参数。 |
| -? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Ftp**命令行参数区分大小写。

- 仅当**Internet 协议（tcp/ip）** 协议安装为网络连接中的网络适配器属性中的组件时，此命令才可用。

- **Ftp**命令可以交互方式使用。 启动后， **ftp**将创建一个可在其中使用**ftp**命令的子环境。 可以通过键入**quit**命令返回到命令提示符。 当**ftp**子环境正在运行时，它由 `ftp >` 命令提示符指示。 有关详细信息，请参阅**ftp**命令。

- **Ftp**命令支持在安装 ipv6 协议时使用 ipv6。

### <a name="examples"></a>示例

若要登录到名为的 ftp 服务器 `ftp.example.microsoft.com` ，请键入：

```
ftp ftp.example.microsoft.com
```

若要登录到名为的 ftp 服务器 `ftp.example.microsoft.com` 并运行名为*resync .txt*的文件中包含的**ftp**命令，请键入：

```
ftp -s:resync.txt ftp.example.microsoft.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))

- [IP 版本6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738636(v=ws.10))

- [IPv6 应用程序](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782509(v=ws.10))
