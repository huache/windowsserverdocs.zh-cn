---
title: finger
description: Finger 命令的参考文章，其中显示了有关运行 finger 服务或后台程序的指定远程计算机上的用户的信息。
ms.topic: article
ms.assetid: 907ea637-5c6c-4752-84c2-46bbf2a68a33
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 503b431905d764d371bff0c69eef9032fb0c8644
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890201"
---
# <a name="finger"></a>finger

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定远程计算机上的用户的信息， (通常是运行 UNIX) 运行 finger 服务或后台程序的计算机。 远程计算机指定用户信息显示的格式和输出。 使用不带参数的**指针**会显示帮助。

> [!IMPORTANT]
> 仅当在 "网络连接" 中网络适配器的属性中将 "Internet 协议" (TCP/IP) 协议安装为组件时，此命令才可用。

## <a name="syntax"></a>语法

```
finger [-l] [<user>] [@<host>] [...]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| -l | 以长列表格式显示用户信息。 |
| `<user>` | 指定您要了解其信息的用户。 如果省略*user*参数，此命令将显示有关指定计算机上的所有用户的信息。 |
| `@<host>` | 指定运行 finger 服务的远程计算机，在该计算机上查找用户信息。 可以指定计算机名称或 IP 地址。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 必须使用连字符 (-) 而不是斜杠 (/) 为**手指**参数加前缀。

- `user@host`可以指定多个参数。

### <a name="examples"></a>示例

若要在计算机*users.microsoft.com*上显示*user1*的信息，请键入：

```
finger user1@users.microsoft.com
```

若要显示计算机*users.microsoft.com*上*所有用户*的信息，请键入：

```
finger @users.microsoft.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
