---
title: mount
description: 用于装载网络文件系统（NFS）网络共享的 mount 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dd9d7ecb-ef00-4aaa-bcd0-423fa636e34a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 823b88b8ab1168776c25e05e3dbf5ec08d784724
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354557"
---
# <a name="mount"></a>mount

用于装载网络文件系统（NFS）网络共享的命令行实用程序。 当不带选项或参数使用时，**装载**会显示有关所有已装载 NFS 文件系统的信息。

> [!NOTE]
> 此实用程序仅在安装了**NFS 客户端**的情况下可用。

## <a name="syntax"></a>语法

```
mount [-o <option>[...]] [-u:<username>] [-p:{<password> | *}] {\\<computername>\<sharename> | <computername>:/<sharename>} {<devicename> | *}
```

### <a name="parameters"></a>参数

| 参数  | 说明 |
| ---------- | ----------- |
| -o rsize =`<buffersize>` | 设置读取缓冲区的大小（kb）。 可接受的值为1、2、4、8、16和 32;默认值为 32 KB。 |
| -o wsize =`<buffersize>` | 设置写入缓冲区的大小（以 kb 为单位）。 可接受的值为1、2、4、8、16和 32;默认值为 32 KB。 |
| -o timeout =`<seconds>` | 设置远程过程调用（RPC）的超时值（以秒为单位）。 可接受的值为0.8、0.9 和范围1-60 内的任何整数;默认值为0.8。 |
| -o retry =`<number>` | 设置软装载的重试次数。 可接受的值为1-10 范围内的整数;默认值为1。 |
| -o mtype =`{soft|hard}` | 设置 NFS 共享的装载类型。 默认情况下，Windows 将使用软装入。 当存在连接问题时，软装载会更容易，但是，为了减少 NFS 服务器重启过程中的 i/o 中断，我们建议使用硬装载。|
| -o anon | 作为匿名用户进行安装。 |
| -o nolock | 禁用锁定（默认为**启用**）。 |
| -o casesensitive | 强制服务器上的文件查找区分大小写。 |
| -o fileaccess =`<mode>` | 指定在 NFS 共享上创建的新文件的默认权限模式。 将*模式*指定为*ogw*形式的三位数字，其中*o*、 *g*和*w*分别表示授予了文件所有者、组和世界的访问权限。 位数必须在0-7 范围内，包括：<ul><li>**0：** 无访问权限</li><li>**1：** x （执行访问）</li><li>**2：** w （写入访问权限）</li><li>**3：** wx （写入和执行访问）</li><li>**4：** r （读取权限）</li><li>**5：** rx （读取和执行访问权限）</li><li>**6：** rw （读取和写入访问权限）</li><li>**7：** rwx （读取、写入和执行访问权限）</li></ul> |
| -o lang =`{euc-jp|euc-tw|euc-kr|shift-jis|Big5|Ksc5601|Gb2312-80|Ansi)` | 指定要在 NFS 共享上配置的语言编码。 只能在共享上使用一种语言。 此值可以包含以下任何值：<ul><li>**euc-jp：** 日语</li><li>**euc-幼圆：** 中文</li><li>**euc-kr：** 朝鲜语</li><li>shift-jis **：** 日语</li><li>**Big5：** 中文</li><li>**Ksc5601：** 朝鲜语</li><li>**Gb2312-80：** 简体中文</li><li>**Ansi：** ANSI 编码</li></ul> |
| 形`<username>` | 指定用于装载共享的用户名。 如果*用户名*前面没有反斜杠（* *\** ），则将其视为 UNIX 用户名。 |
| h-p`<password>` | 用于装载共享的密码。 如果使用星号（**&#42;**），系统会提示输入密码。 |
| `<computername>` | 指定 NFS 服务器的名称。 |
| `<sharename>` | 指定文件系统的名称。 |
| `<devicename>` | 指定设备的驱动器号和名称。 如果使用星号（**&#42;**），则此值表示第一个可用的驱动程序号。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
