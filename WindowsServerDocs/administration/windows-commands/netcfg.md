---
title: netcfg
description: Netcfg 命令的参考文章，其中安装了用于部署工作站的 Windows 轻型版本 (WinPE) Windows 预安装环境。
ms.topic: reference
ms.assetid: e2daaab7-12db-4e36-b70c-db8906d084f7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f2238fcde1de109298801fea985100bffabf8f7
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038808"
---
# <a name="netcfg"></a>netcfg

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

安装 Windows 预安装环境 (WinPE) ，这是用于部署工作站的 Windows 轻型版本。

## <a name="syntax"></a>语法

```
netcfg [/v] [/e] [/winpe] [/l ] /c /i
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /v | 在详细 (详细) 模式下运行。 |
| /e | 在安装和卸载过程中使用服务环境变量。 |
| /winpe |  (WinPE) 安装 TCP/IP、NetBIOS 和 Microsoft 客户端 Windows 预安装环境。 |
| /l | 提供 INF 文件的位置。 |
| /c | 提供要安装的组件的类; **协议**、 **服务**或 **客户端**。 |
| /i | 提供组件 ID。 |
| /s | 提供要显示的组件类型，包括适配器的 **\ta** 或 net 组件的 **n** 。 |
| /b | 显示绑定路径，后跟包含路径名称的字符串。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要使用 c:\oemdir\example.inf 安装协议 *示例* ，请键入：

```
netcfg /l c:\oemdir\example.inf /c p /i example
```

若要安装 *MS_Server* 服务，请键入：

```
netcfg /c s /i MS_Server
```

若要安装 TCP/IP、NetBIOS 和适用于 Windows 预安装环境的 Microsoft 客户端，请键入：

```
netcfg /v /winpe
```

若要显示组件 *MS_IPX* 是否已安装，请键入：

```
netcfg /q MS_IPX
```

若要卸载组件 *MS_IPX*，请键入：

```
netcfg /u MS_IPX
```

若要显示所有已安装的网络组件，请键入：

```
netcfg /s n
```

若要显示包含 *MS_TCPIP*的绑定路径，请键入：

```
netcfg /b ms_tcpip
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
