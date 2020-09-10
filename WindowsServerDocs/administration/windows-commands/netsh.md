---
title: netsh
description: Netsh 命令的参考文章，这是一个命令行脚本实用工具，可让你以本地或远程方式显示或修改当前正在运行的计算机的网络配置。
ms.topic: reference
ms.assetid: 96fc069d-53c0-4d0a-9f7f-f9f3d49a02bd carmonmills
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e848003ced9161f0ae07778a2a16d50b7e97d51c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635861"
---
# <a name="netsh"></a>netsh

> 适用于：Windows Server（半年频道）、Windows Server 2016

网络 Shell 命令行脚本实用工具，可让你以本地或远程方式显示或修改当前正在运行的计算机的网络配置。 可以在命令提示符下或在 Windows PowerShell 中启动此实用工具。

## <a name="syntax"></a>语法

```
netsh [-a <Aliasfile>][-c <Context>][-r <Remotecomputer>][-u [<domainname>\<username>][-p <Password> | [{<NetshCommand> | -f <scriptfile>}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -a `<Aliasfile>` | 指定在运行 Aliasfile 后返回到 netsh 提示符，并指定包含一个或多个 netsh 命令的文本文件的名称。 |
| -c `<Context>` | 指定 netsh 输入指定的 netsh 上下文和 netsh 上下文来输入。 |
| -r `<Remotecomputer>` | 指定要配置的远程计算机。<p>**重要提示：** 如果使用此参数，则必须确保远程计算机上正在运行远程注册表服务。 如果未运行，Windows 将显示 "找不到网络路径" 错误消息。 |
| -u `<domainname>\<username>` | 指定在用户帐户下运行 netsh 命令时要使用的域和用户帐户名称。 如果省略域，则默认情况下使用本地域。 |
| -p `<Password>` | 指定参数所指定的用户帐户的密码 `-u <username>` 。 |
| `<NetshCommand>` | 指定要运行的 netsh 命令。 |
| -f `<scriptfile>` | 运行指定的脚本文件后退出 netsh 命令。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果指定 **-r** 后跟另一个命令，则 netsh 会在远程计算机上运行该命令，然后返回到 Cmd.exe 命令提示符。 如果指定 **-r** 而不包含其他命令，则 netsh 将以远程模式打开。 此过程类似于在 Netsh 命令提示符下使用 set machine  。 使用 **-r**时，只会为当前 netsh 实例设置目标计算机。 退出并重新输入 netsh 后，目标计算机将重置为本地计算机  。 通过指定存储在 WINS 中的计算机名称、UNC 名称、DNS 服务器要解析的 Internet 名称或 IP 地址，可以在远程计算机上运行 netsh 命令  。

- 如果字符串值包含空格，则必须用引号将字符串值引起来。 例如： `-r "contoso remote device"`

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
