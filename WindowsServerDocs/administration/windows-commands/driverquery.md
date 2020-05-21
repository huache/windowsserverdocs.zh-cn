---
title: driverquery
description: Driverquery 命令的参考主题，它使管理员能够显示已安装设备驱动程序及其属性的列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 92ca4b84-e4e2-405b-9f31-bf6db9f66839
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f4754cba8cf4cb3a5f01b0aeb0095f727a072a5c
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436932"
---
# <a name="driverquery"></a>driverquery

使管理员能够显示已安装设备驱动程序及其属性的列表。 如果在没有参数的情况下使用，则**driverquery**将在本地计算机上运行。

## <a name="syntax"></a>语法

```
driverquery [/s <system> [/u [<domain>\]<username> [/p <password>]]] [/fo {table | list | csv}] [/nh] [/v | /si]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| /s`<system>` | 指定远程计算机的名称或 IP 地址。 不要使用反斜杠。 默认值为本地计算机。 |
| /u`[<domain>]<username>` | 使用用户或*域 \**用户指定*的用户帐户的凭据运行该命令。 默认情况下， */s*使用当前登录到发出命令的计算机的用户的凭据。 除非指定 **/s** ，否则不能使用 **/u** 。 |
| /p`<password>` | 指定在 **/u**参数中指定的用户帐户的密码。 除非指定 **/u** ，否则不能使用 **/p** 。 |
| /fo 表 | 将输出的格式设置为一个表。 这是默认设置。 |
| /fo list | 将输出的格式设置为列表。 |
| /fo csv | 将输出的格式设置为逗号分隔值。 |
| /nh | 省略显示的驱动程序信息中的标题行。 如果 **/fo**参数设置为**list**，则无效。 |
| /v | 显示详细输出。 **/v**对于签名的驱动程序无效。 |
| /si | 提供有关签名驱动程序的信息。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要在本地计算机上显示已安装设备驱动程序的列表，请键入：

```
driverquery
```

若要以逗号分隔值（CSV）格式显示输出，请键入：

```
driverquery /fo csv
```

若要在输出中隐藏标题行，请键入：

```
driverquery /nh
```

若要在本地计算机上使用当前凭据在名为*server1*的远程服务器上使用**driverquery**命令，请键入：

```
driverquery /s server1
```

若要在名为*server1*的远程服务器上使用域*maindom*上*user1*的凭据的**driverquery**命令，请键入：

```
driverquery /s server1 /u maindom\user1 /p p@ssw3d
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)