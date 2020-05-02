---
title: mapadmin
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b17332c7-8622-4223-9c43-2fb9cf4d992d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 19975f6f4e0e49cf55e4e80f6566f8596d6d33d8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724026"
---
# <a name="mapadmin"></a>mapadmin



你可以使用**Mapadmin**来管理用于网络文件系统的 Microsoft 服务用户名映射。

## <a name="syntax"></a>语法
```
mapadmin [<computer>] [-u <user> [-p <password>]]
mapadmin [<computer>] [-u <user> [-p <password>]] {start | stop}
mapadmin [<computer>] [-u <user> [-p <password>]] config <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] add -wu <WindowsUser> -uu <UNIXUser> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] add -wg <WindowsGroup> -ug <UNIXGroup> [-setprimary]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wu <WindowsUser> [-uu <UNIXUser>]
mapadmin [<computer>] [-u <user> [-p <password>]] setprimary -wg <WindowsGroup> [-ug <UNIXGroup>]
mapadmin [<computer>] [-u <user> [-p <password>]] delete <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] list <option[...]>
mapadmin [<computer>] [-u <user> [-p <password>]] backup <filename> 
mapadmin [<computer>] [-u <user> [-p <password>]] restore <filename>
mapadmin [<computer>] [-u <user> [-p <password>]] adddomainmap -d <WindowsDomain> {-y <<NISdomain>> | -f <path>}
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -d <WindowsDomain> -y <<NISdomain>>
mapadmin [<computer>] [-u <user> [-p <password>]] removedomainmap -all
mapadmin [<computer>] [-u <user> [-p <password>]] listdomainmaps
```

## <a name="description"></a>说明
**Mapadmin**命令行实用工具在运行 Microsoft Network File System 服务的本地或远程计算机上管理用户名映射。 如果你使用没有管理凭据的帐户登录，则可以指定帐户的用户名和密码。

除了特定的命令参数外， **mapadmin**还接受以下参数和选项：

&lt;计算机&gt;指定运行你要管理的用户名映射服务的远程计算机。 可以使用 Windows Internet 名称服务（WINS）名称或域名系统（DNS）名称或 Internet 协议（IP）地址指定计算机。

-u &lt;用户&gt;指定要使用其凭据的用户的用户名。 可能需要以 "<em>域</em>**\\**<em>用户名</em>" 格式将域名添加到用户名。

-p &lt;password&gt;指定用户的密码。 如果指定 **-u**选项，但忽略 **-p**选项，则系统会提示输入用户的密码。
**Mapadmin**执行的具体操作取决于您指定的命令参数：

### <a name="parameters"></a>参数
### <a name="start"></a>start
启动用户名映射服务。

### <a name="stop"></a>stop
停止用户名映射服务。

### <a name="config"></a>config
指定用户名映射的常规设置。 以下选项可用于此命令参数： **-r &lt;&gt;dddd：&lt;hh&gt;：&lt;mm&gt; ** -指定从 Windows 和 NIS 数据库更新的刷新间隔（以天、小时和分钟为单位）。 最小间隔为5分钟。
**-i {yes | no}** -打开（**yes**）或 off （**no**）简单映射。 默认情况下，简单映射为 on。
**添加**-为用户或组创建新映射。 以下选项可用于此命令参数：

|选项|定义|
|-----|-------|
|-wu &lt;名称&gt;|指定要为其创建新映射的 Windows 用户的名称。|
|-uu &lt;name&gt;|指定正在为其创建新映射的 UNIX 用户的名称。|
|-wg &lt;组&gt;|指定要为其创建新映射的 Windows 组的名称。|
|-buj-ug-pkt &lt;组&gt;|指定要为其创建新映射的 UNIX 组的名称。|
|-setprimary|指定新的映射为主映射。|

**setprimary** -指定使用多个映射的 UNIX 用户或组的主映射。 以下选项可用于此命令参数：

|选项|定义|
|-----|-------|
|-wu &lt;名称&gt;|指定主映射的 Windows 用户。 如果该用户存在多个映射，请使用 **-uu**选项来指定主映射。|
|-uu &lt;name&gt;|指定主映射的 UNIX 用户。|
|-wg &lt;组&gt;|指定主映射的 Windows 组。 如果该组存在多个映射，请使用 **-buj-ug-pkt**选项指定主映射。|
|-buj-ug-pkt &lt;组&gt;|指定主映射的 UNIX 组。|

**删除**-删除用户或组的映射。 以下选项可用于此命令参数：

|选项|定义|
|-----|-------|
|-wu &lt;用户&gt;|要为其删除映射的 Windows 用户，将指定为&lt; *WindowsDomain&gt;\\&lt;用户名&gt;*。 必须指定 **-wu**或 **-uu**选项，或同时指定两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-wu**选项，则将删除指定用户的所有映射。|
|-wg &lt;组&gt;|将为其删除映射的 Windows 组，并将其指定&lt;为&gt;\\&lt;WindowsDomain&gt;组名。 必须指定 **-wg**或 **-buj-ug-pkt**选项，或同时指定这两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-wg**选项，则将删除指定组的所有映射。|
|-uu &lt;用户&gt;|将为其删除映射的 UNIX 用户，指定为&lt;"用户名"。&gt; 必须指定 **-wu**或 **-uu**选项，或同时指定两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-uu**选项，则将删除指定用户的所有映射。|
|-buj-ug-pkt &lt;组&gt;|将为其删除映射的 UNIX 组，指定为&lt;组名。&gt; 必须指定 **-wg**或 **-buj-ug-pkt**选项，或同时指定这两者。 如果指定这两个选项，则将删除由两个选项标识的特定映射。 如果只指定 **-buj-ug-pkt**选项，则将删除指定组的所有映射。|

**列表**-显示有关用户和组映射的信息。 以下选项可用于此命令参数：

|选项|定义|
|-----|-------|
|-所有|列出用户和组的简单和高级映射。|
|-简单|列出所有简单的映射用户和组。|
|-高级|列出所有高级映射的用户和组。 映射按照其计算顺序列出。 以星号（*）标记的主映射首先列出，后跟辅助地图，它们标记有克拉（^）。|
|-wu &lt;名称&gt;|列出指定 Windows 用户的映射。|
|-wg &lt;组&gt;|列出 Windows 组的映射。|
|-uu &lt;name&gt;|列出 UNIX 用户的映射。|
|-buj-ug-pkt &lt;组&gt;|列出 UNIX 组的映射。|

**备份**-将用户名映射配置和映射数据保存到&lt;文件名&gt;指定的文件中。
**还原**-使用备份命令参数创建的文件中的数据（由&lt;文件名&gt;指定）替换配置和映射数据**backup** 。
**adddomainmap** -在 Windows 域和 NIS 域或密码与组文件之间添加简单映射。 以下选项可用于此命令参数：

|选项|定义|
|-----|-------|
|-d &lt;WindowsDomain&gt;|指定要映射的 Windows 域。|
|-y &lt;NISdomain&gt;|指定要映射的 NIS 域。&lt;br/&gt;&lt;br/&gt;**-n** &lt;nisServer&gt;指定用 **-y**选项指定的 nis 域的 nis 服务器。|
|-f &lt;路径&gt;|指定包含要映射的密码和组文件的目录的完全限定路径。 文件必须位于被管理的计算机上，并且你无法使用**mapadmin**来管理远程计算机，以根据密码和组文件设置映射。|

**removedomainmap** -删除 Windows 域和 NIS 域之间的简单映射。 以下选项和参数可用于此命令参数：

|选项|定义|
|-----|-------|
|-d &lt;WindowsDomain&gt;|指定要删除的映射的 Windows 域。|
|-y &lt;NISdomain&gt;|指定要删除的映射的 NIS 域。|
|-所有|指定将删除 Windows 和 NIS 域之间的所有简单映射。 这也会删除 Windows 域和密码与组文件之间的任何简单映射。|

**listdomainmaps** -列出映射到 NIS 域或密码和组文件的 Windows 域。

## <a name="notes"></a>说明
-   如果未指定命令参数，则**mapadmin**将显示用户名映射的当前设置。
-   对于指定用户或组名称的所有选项，可以使用以下格式：
-   对于 Windows 用户，请使用窗&lt;体&gt;\\&lt;域用户名&gt;、 \\ \\ &lt;计算机&gt;\\&lt;&gt;用户名\\ &lt;&gt;\\、&lt;计算机&gt;用户名或&lt;计算机&gt;用户名\\&lt;&gt;
-   对于 Windows 组，请使用表单&lt;域&gt;\\&lt;&lt;&gt;&gt;组组\\ \\ &lt;、&gt;\\&lt;计算机&gt;&lt;组名、&gt;计算机&gt;组名或&lt;计算机&gt;组\\\\&lt;&gt;&lt; &lt;&gt;&lt; \\&lt;&gt;&gt;
-   对于 UNIX 用户，请使用格式&lt;NISdomain&gt;\\&lt;用户名&gt; &lt;、用户名&gt;@&lt;&gt;NISdomain、 &lt;用户名&gt;@PCNFS或 PCNFS\\&lt;用户名&gt;
-   对于 UNIX 组，请使用 NISdomain &lt;&gt;\\&lt;&gt; &lt;&gt;@&lt;组组、组名\\或 PCNFS 组的形式&lt;&gt; &lt;&gt;@PCNFS&gt;

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
