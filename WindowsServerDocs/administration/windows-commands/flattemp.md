---
title: flattemp
description: Flattemp 命令的参考文章，用于启用或禁用平面临时文件夹。
ms.topic: reference
ms.assetid: 059a0960-1fd9-4382-87fe-a85d5dccdaea
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 86fcad8a22c73aa8682059f657966c9ac20b8793
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634872"
---
# <a name="flattemp"></a>flattemp

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启用或禁用平面临时文件夹。 您必须具有管理凭据才能运行此命令。

> [!NOTE]
> 仅当你已安装远程桌面会话主机角色服务时，此命令才可用。

## <a name="syntax"></a>语法

```
flattemp {/query | /enable | /disable}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /query | 查询当前设置。 |
| /enable | 启用单层临时文件夹。 用户将共享临时文件夹，除非临时文件夹位于用户的主文件夹中。 |
| /disable | 禁用平面临时文件夹。 每个用户的临时文件夹将位于单独的文件夹中 (由用户的会话 ID) 确定。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 每个用户都有一个唯一的临时文件夹后，使用 `flattemp /enable` 来启用单层临时文件夹。

- 用于为多个用户创建临时文件夹 (通常由 TEMP 和 TMP 环境变量指向的默认方法) 是在 **\temp** 文件夹中创建子文件夹，方法是使用 logonID 作为子文件夹名称。 例如，如果 TEMP 环境变量指向 C：\Temp，则分配给 user logonID 4 的临时文件夹为 C:\Temp\4。

    使用 **flattemp**，可以直接指向 \temp 文件夹，防止子文件夹形成。 如果希望将用户临时文件夹包含在主文件夹中（无论是在远程桌面会话主机服务器本地驱动器上，还是位于共享的网络驱动器上），这会很有用。 `flattemp /enable*`仅当每个用户都有单独的临时文件夹时，才应使用命令。

- 如果用户的临时文件夹位于网络驱动器上，则可能会遇到应用错误。 如果网络上的共享网络驱动器暂时无法访问，则会发生这种情况。 由于应用程序的临时文件无法访问或不同步，因此它将作为磁盘停止的响应。 建议不要将临时文件夹移动到网络驱动器。 默认情况下，将临时文件夹保留在本地硬盘上。 如果遇到与某些应用程序有关的意外行为或磁盘损坏错误，请使网络稳定，或将临时文件夹移回本地硬盘。

- 如果禁用每个会话使用单独的临时文件夹，则将忽略 **flattemp** 设置。 此选项在远程桌面服务配置工具中设置。

### <a name="examples"></a>示例

若要显示单层临时文件夹的当前设置，请键入：

```
flattemp /query
```

若要启用平面临时文件夹，请键入：

```
flattemp /enable
```

若要禁用平面临时文件夹，请键入：

```
flattemp /disable
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

