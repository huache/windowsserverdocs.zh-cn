---
title: ftp open
description: 用于连接到指定 ftp 服务器的 ftp open 命令的参考文章。
ms.topic: reference
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 24fabf61e57a0dda00837a15702dfe9ef5ee6862
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635288"
---
# <a name="ftp-open"></a>ftp open

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

连接到指定的 ftp 服务器。

## <a name="syntax"></a>语法

```
open <computer> [<port>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<computer>` | 指定您尝试连接到的远程计算机。 您可以使用 IP 地址或计算机名称 (在这种情况下，DNS 服务器或主机文件必须) 可用。 |
| `[<port>]` | 指定用于连接到 ftp 服务器的 TCP 端口号。 默认情况下，使用 TCP 端口21。 |

### <a name="examples"></a>示例

若要在 *ftp.microsoft.com*连接到 ftp 服务器，请键入：

```
open ftp.microsoft.com
```

若要连接到侦听 TCP 端口*755*的*ftp.microsoft.com*上的 ftp 服务器，请键入：

```
open ftp.microsoft.com 755
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
