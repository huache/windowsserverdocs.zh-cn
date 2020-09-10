---
title: nfsshare
description: 用于控制网络文件系统 (NFS) 共享的 nfsshare 命令的参考文章。
ms.topic: reference
ms.assetid: 437a2615-335a-442f-9713-d50d5f3983a3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f41c9e4dfd14219ceac9c42741d372beb8defb9b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635810"
---
# <a name="nfsshare"></a>nfsshare

控制网络文件系统 (NFS) 共享。 使用没有参数的情况下，此命令将显示 NFS 服务器导出的所有网络文件系统 (NFS) 共享。

## <a name="syntax"></a>语法

```
nfsshare <sharename>=<drive:path> [-o <option=value>...]
nfsshare {<sharename> | <drive>:<path> | * } /delete
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -o anon =`{yes|no}` | 指定匿名 (是否) 用户可以访问共享目录。 |
| -o rw =`[<host>[:<host>]...]` | 提供由 *主机*指定的主机或客户端组对共享目录的读写访问权限。 必须用冒号 (**：**) 分隔主机名和组名。 如果未指定 *主机* ，则除使用 **ro** 选项指定的主机和客户端组外，所有主机和客户端 (组) 获取读写访问权限。 如果不设置 **ro** 或 **rw** 选项，所有客户端都具有对共享目录的读写访问权限。 |
| -o ro =`[<host>[:<host>]...]` | 提供由 *主机*指定的主机或客户端组对共享目录的只读访问。 必须用冒号 (**：**) 分隔主机名和组名。 如果未指定 *主机* ，则除使用 **rw** 选项指定的客户端之外的所有客户 (端) 获取只读访问权限。 如果为一个或多个客户端设置了 **ro** 选项，但未设置 **rw** 选项，则只有使用 **ro** 选项指定的客户端才能访问共享目录。 |
| -o 编码 =`{euc-jp|euc-tw|euc-kr|shift-jis|Big5|Ksc5601|Gb2312-80|Ansi)` | 指定要在 NFS 共享上配置的语言编码。 只能在共享上使用一种语言。 此值可以包含以下任何值：<ul><li>**euc-jp：** 日语</li><li>**euc-幼圆：** 中文</li><li>**euc-kr：** 朝鲜语</li><li>shift-jis **：** 日语</li><li>**Big5：** 中文</li><li>**Ksc5601：** 朝鲜语</li><li>**Gb2312-80：** 简体中文</li><li>**Ansi：** ANSI 编码</li></ul> |
| -o anongid =`<gid>` | 指定匿名 (取消映射) 用户使用 *gid* 作为其组标识符 (gid) 来访问共享目录。 默认值为 **-2**。 在报告未映射用户拥有的文件的所有者时，即使禁用匿名访问，也将使用匿名 GID。 |
| -o anonuid =`<uid>` | 指定匿名 (取消映射) 用户使用 *uid* 作为其用户标识符 (uid) 来访问共享目录。 默认值为 **-2**。 在报告未映射用户拥有的文件的所有者时，即使禁用匿名访问，也将使用匿名 UID。 |
| -o root =`[<host>[:<host>]...]` | 提供由 *主机*指定的主机或客户端组对共享目录的根访问权限。 必须用冒号 (**：**) 分隔主机名和组名。 如果未指定 *主机* ，则所有客户端均获取根访问权限。 如果未设置 **根** 选项，则没有客户端具有对共享目录的根访问权限。 |
| /delete | 如果已指定共享 *名* 或 `<drive>:<path>` ，则此参数将删除指定的共享。 如果指定了通配符 ( * ) ，则此参数将删除所有 NFS 共享。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果 *共享名* 是唯一的参数，此命令将列出由 *共享名*标识的 NFS 共享的属性。

- 如果使用了 *共享名* 和 `<drive>:<path>` ，则此命令会将标识的文件夹导出 `<drive>:<path>` 为 *共享名*。 如果使用 **/delete** 选项，则指定的文件夹停止可用于 NFS 客户端。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [网络文件系统命令参考服务](services-for-network-file-system-command-reference.md)

- [NFS cmdlet 参考](/powershell/module/nfs)
