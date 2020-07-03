---
title: freedisk
description: Freedisk 命令的参考文章，用于检查是否有指定数量的可用磁盘空间，然后再继续执行安装过程。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 91c15166-5baa-4b80-9e0c-4cd815d00530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0cfce52c2eaf0917f8169d959b61832bd1779e0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924746"
---
# <a name="freedisk"></a>freedisk

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在继续执行安装过程之前，检查是否有指定数量的可用磁盘空间。

## <a name="syntax"></a>语法

```
freedisk [/s <computer> [/u [<domain>\]<user> [/p [<password>]]]] [/d <drive>] [<value>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /s`<computer>` | 指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认为本地计算机。 此参数适用于命令中指定的所有文件和文件夹。 |
| /u`[<domain>\]<user>` | 用指定用户帐户的权限运行脚本。 默认值为 "系统权限"。 |
| /p [ <password> ] | 指定在 **/u**中指定的用户帐户的密码。 |
| /d`<drive>` | 指定要找出可用空间可用性的驱动器。 您必须 `<drive>` 为远程计算机指定。 |
| `<value>` | 检查特定的可用磁盘空间量。 可以指定 `<value>` 字节、KB、MB、GB、TB、PB、EB、ZB 或 YB。 |

#### <a name="remarks"></a>备注

- 仅当使用 **/s**时，才能使用 **/s**、 **/u**和 **/p**命令行选项。 必须使用 **/p** with **/u**来提供用户的密码。

- 对于无人参与的安装，可以在安装批处理文件中使用**freedisk**来检查必备空间可用空间，然后再继续安装。

- 在批处理文件中使用**freedisk**时，如果有足够的空间，则返回**0** ; 如果空间不足，则返回**1** 。

### <a name="examples"></a>示例

若要确定驱动器 C：上是否有至少 50 MB 的可用空间，请键入：

```
freedisk 50mb
```

屏幕上会显示类似于以下内容的输出：

```
INFO: The specified 52,428,800 byte(s) of free space is available on current drive.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
