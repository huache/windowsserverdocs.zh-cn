---
title: getmac
description: Getmac 命令的参考文章，该命令返回媒体访问控制（MAC）地址，以及与每个、本地或跨网络相关联的网络协议列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 345daa310b075f8a094dd8a87e7c1c0d3694ab10
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932345"
---
# <a name="getmac"></a>getmac

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

返回与每台计算机的所有网卡的每个地址相关联的媒体访问控制（MAC）地址和网络协议列表，不管是在本地还是在网络上。 当你希望将 MAC 地址输入网络分析器时，或者需要知道计算机上的每个网络适配器当前正在使用的协议时，此命令特别有用。

## <a name="syntax"></a>语法

```
getmac[.exe][/s <computer> [/u <domain\<user> [/p <password>]]][/fo {table | list | csv}][/nh][/v]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| /s`<computer>` | 指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认为本地计算机。 |
| /u`<domain>\<user>` | 使用*user*或*domain\user*指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
| /p`<password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| /fo {table | list | .csv | 指定用于查询输出的格式。 有效值为**table**、 **list**和**csv**。 输出的默认格式为**table**。 |
| /nh | 隐藏输出中的列标题。 当 **/fo**参数设置为**表**或**csv**时有效。 |
| /v | 指定输出显示详细信息。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

下面的示例演示如何使用**getmac**命令：

```
getmac /fo table /nh /v
```

```
getmac /s srvmain
```

```
getmac /s srvmain /u maindom\hiropln
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo list /v
```

```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo table /nh
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
