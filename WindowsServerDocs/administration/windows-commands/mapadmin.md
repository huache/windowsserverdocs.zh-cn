---
title: mapadmin
description: Mapadmin 命令的参考文章，用于管理用于网络文件系统的 Microsoft 服务用户名映射。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b17332c7-8622-4223-9c43-2fb9cf4d992d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2ebe5626057bd7f7ddac238360d171c87fd15c6
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922184"
---
# <a name="mapadmin"></a>mapadmin

**Mapadmin**命令行实用工具在运行 Microsoft Network File System 服务的本地或远程计算机上管理用户名映射。 如果你使用没有管理凭据的帐户登录，则可以指定帐户的用户名和密码。

## <a name="syntax"></a>语法

```
mapadmin [<computer>] [-u <user> [-p <password>]]
mapadmin [<computer>] [-u <user> [-p <password>]] {start | stop}
mapadmin [<computer>] [-u <user> [-p <password>]] config <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] add -wu <windowsuser> -uu <UNIXuser> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] add -wg <windowsgroup> -ug <UNIXgroup> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wu <Windowsuser> [-uu <UNIXuser>]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wg <Windowsgroup> [-ug <UNIXgroup>]
mapadmin [<computer>] [-u <user> [-p <password>]] delete <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] list <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] backup <filename>
mapadmin [<computer>] [-u <user> [-p <password>]] restore <filename>
mapadmin [<computer>] [-u <user> [-p <password>]] adddomainmap -d <Windowsdomain> {-y <<NISdomain>> | -f <path>}
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -d <Windowsdomain> -y <<NISdomain>>
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -all
mapadmin [<computer>] [-u <user> [-p <password>]] listdomainmaps
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<computer>` | 指定运行要管理的用户名映射服务的远程计算机。 可以使用 Windows Internet 名称服务（WINS）名称或域名系统（DNS）名称或 Internet 协议（IP）地址指定计算机。 |
| -u`<user>` | 指定要使用其凭据的用户的用户名。 可能需要以 "域*\ 用户名*" 格式将域名添加到用户名。 |
| -p`<password>` | 指定用户的密码。 如果指定 **-u**选项，但忽略 **-p**选项，则系统会提示输入用户的密码。 |
| `start | stop` | 启动或停止用户名映射服务。 |
| config | 指定用户名映射的常规设置。 此参数提供以下选项：<ul><li>**-r `<dddd>:<hh>:<mm>` ：** 指定从 Windows 和 NIS 数据库更新的刷新间隔（以天、小时和分钟为单位）。 最小间隔为5分钟。</li><li>**-i `{yes | no}` ：** 打开（**yes**）或 off （**no**）简单映射。 默认情况下，将启用映射。</li></ul> |
| add | 为用户或组创建新的映射。 此参数提供以下选项：<ul><li>**-wu `<name>` ：** 指定正在为其创建新映射的 Windows 用户的名称。</li><li>**-uu `<name>` ：** 指定正在为其创建新映射的 UNIX 用户的名称。</li><li>**-wg `<group>` ：** 指定正在为其创建新映射的 Windows 组的名称。</li><li>**-buj-ug-pkt `<group>` ：** 指定要为其创建新映射的 UNIX 组的名称。</li><li>**-setprimary：** 指定新的映射为主映射。</li></ul> |
| setprimary | 指定哪个映射是包含多个映射的 UNIX 用户或组的主映射。 此参数提供以下选项：<ul><li>**-wu `<name>` ：** 指定主映射的 Windows 用户。 如果该用户存在多个映射，请使用 **-uu**选项来指定主映射。</li><li>**-uu `<name>` ：** 指定主映射的 UNIX 用户。</li><li>**-wg `<group>` ：** 指定主映射的 Windows 组。 如果该组存在多个映射，请使用 **-buj-ug-pkt**选项指定主映射。</li><li>**-buj-ug-pkt `<group>` ：** 指定主映射的 UNIX 组。</li></ul> |
| delete | 删除用户或组的映射。 以下选项可用于此参数：<ul><li>**-wu `<user>` ：** 指定要为其删除映射的 Windows 用户，将指定为 `<windowsdomain>\<username>` 。<p>必须指定 **-wu**或 **-uu**选项，或同时指定两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-wu**选项，则将删除指定用户的所有映射。</li><li>**-uu `<user>` ：** 指定要为其删除映射的 UNIX 用户，将指定为 `<username>` 。<p>必须指定 **-wu**或 **-uu**选项，或同时指定两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-uu**选项，则将删除指定用户的所有映射。</li><li>**-wg `<group>` ：** 指定要为其删除映射的 Windows 组，将指定为 `<windowsdomain>\<username>` 。<p>必须指定 **-wg**或 **-buj-ug-pkt**选项，或同时指定这两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-wg**选项，则将删除指定组的所有映射。</li><li>**-buj-ug-pkt `<group>` ：** 指定要为其删除映射的 UNIX 组，将指定为 `<groupname>` 。<p>必须指定 **-wg**或 **-buj-ug-pkt**选项，或同时指定这两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-buj-ug-pkt**选项，则将删除指定组的所有映射。</li></ul> |
| list | 显示有关用户和组映射的信息。 此参数提供以下选项：<ul><li>**-all：** 列出用户和组的简单和高级映射。</li><li>**-简单：** 列出所有简单的映射用户和组。</li><li>**-高级：** 列出所有高级映射的用户和组。 映射按照其计算顺序列出。 用星号（）标记的主映射*首先列出，然后是以克拉标记的辅助地图 `(^)` 。 </li> <li>* *-wu `<name>` ：** 列出指定 Windows 用户的映射。</li><li>**-wg `<group>` ：** 列出 Windows 组的映射。</li><li>**-uu `<name>` ：** 列出 UNIX 用户的映射。</li><li>**-buj-ug-pkt `<group>` ：** 列出 UNIX 组的映射。</li></ul> |
| backup | 将用户名映射配置和映射数据保存到指定的文件 `<filename>` 。 |
| 还原 | 将配置和映射数据替换为 `<filename>` 使用**backup**参数创建的文件中的数据（由指定）。 |
| adddomainmap | 在 Windows 域和 NIS 域或密码与组文件之间添加简单映射。 以下选项可用于此参数：<ul><li>**-d `<windowsdomain>` ：** 指定要映射的 Windows 域。</li><li>**-y `<NISdomain>` ：** 指定要映射的 NIS 域。 必须使用 **-n `<NISserver>` **参数指定由 **-y**选项指定的 nis 域的 nis 服务器。</li><li>**-f `<path>` ：** 指定目录的完全限定路径，该路径包含要映射的密码和组文件。 文件必须位于被管理的计算机上，并且你无法使用**mapadmin**来管理远程计算机，以根据密码和组文件设置映射。</li></ul> |
| removedomainmap | 删除 Windows 域和 NIS 域之间的简单映射。 以下选项和参数可用于此参数：<ul><li>**-d `<windowsdomain>` ：** 指定要删除的映射的 Windows 域。</li><li>**-y `<NISdomain>` ：** 指定要删除的映射的 NIS 域。</li><li>**-all：** 指定将删除 Windows 和 NIS 域之间的所有简单映射。 这也会删除 Windows 域和密码与组文件之间的任何简单映射。</li></ul> |
| listdomainmaps | 列出映射到 NIS 域或密码和组文件的 Windows 域。 |

#### <a name="remarks"></a>备注

- 如果未指定任何参数，则**mapadmin**命令将显示用户名映射的当前设置。

- 对于指定用户或组名称的所有选项，可以使用以下格式：

    - 对于 Windows 用户，请使用以下格式： `<domain>\<username>` 、 `\\<computer>\<username>` 、 `\<computer>\<username>` 或`<computer>\<username>`

    - 对于 Windows 组，请使用以下格式： `<domain>\<groupname>` 、 `\\<computer>\<groupname>` 、 `\<computer>\<groupname>` 或`<computer>\<groupname>`

    - 对于 UNIX 用户，请使用以下格式： `<NISdomain>\<username>` 、 `<username>@<NISdomain>` 、 `<username>@PCNFS` 或`PCNFS\<username>`

    - 对于 UNIX 组，请使用以下格式： `<NISdomain>\<groupname>` 、 `<groupname>@<NISdomain>` 、 `<groupname>@PCNFS` 或`PCNFS\<groupname>`

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
