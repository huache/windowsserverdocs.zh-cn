---
title: macfile
description: Macfile 命令的参考文章，其中管理了 Macintosh 服务器、卷、目录和文件的文件服务器。
ms.topic: article
ms.assetid: e2ce586c-b316-41d3-90f8-4be0d074cc0e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d3b450241ee3f8a765f9ac93ec09b0450d8c28e5
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887047"
---
# <a name="macfile"></a>macfile

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

管理 Macintosh 服务器、卷、目录和文件的文件服务器。 您可以通过在批处理文件中包含一系列命令，然后手动或在预定时间启动它们来自动执行管理任务。

## <a name="modify-directories-in-macintosh-accessible-volumes"></a>修改 Macintosh 中的目录-可访问的卷

更改 Macintosh 可访问卷的目录名称、位置、所有者、组和权限。

### <a name="syntax"></a>语法

```
macfile directory[/server:\\<computername>] /path:<directory> [/owner:<ownername>] [/group:<groupname>] [/permissions:<permissions>]
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /server:`\\<computername>` | 指定要在其上更改目录的服务器。 如果省略，则在本地计算机上执行该操作。 |
| /path`<directory>` | 指定要更改的目录的路径。 此参数是必需的。 **注意：** 该目录必须存在，但使用**macfile 目录**不会创建目录。 |
| /owner`<ownername>` | 更改目录的所有者。 如果省略，所有者名称将不会更改。 |
| 组`<groupname>` | 指定或更改与目录关联的 Macintosh 主组。 如果省略，则主组将保持不变。 |
| 访问`<permissions>` | 为所有者、主要组和世界 (每个人) 的目录设置权限。 这必须是一个11位数，其中，number 1 授予权限，0撤消权限 (例如，11111011000) 。 如果省略此参数，则权限保持不变。 |
| /? | 在命令提示符下显示帮助。 |

##### <a name="position-of-permissions-digit"></a>权限位的位置

权限数字的位置确定设置的权限，包括：

| 位置 | 设置权限 |
| -------- | --------------- |
| First | OwnerSeeFiles |
| 秒 | OwnerSeeFolders |
| 第三个 | OwnerMakechanges |
| 第四个 | GroupSeeFiles |
| 第五个 | GroupSeeFolders |
| 第六个 | GroupMakechanges |
| 第七个 | WorldSeeFiles |
| 第 | WorldSeeFolders |
| 第九个 | WorldMakechanges |
| 十分 | 不能重命名、移动或删除该目录。 |
| 第 | 更改将应用到当前目录和所有子目录。 |

##### <a name="remarks"></a>备注

- 如果提供的信息包含空格或特殊字符，请在文本两侧使用引号 (例如，" `<computer name>` " ) 。

- 使用**macfile 目录**将可供 macintosh 用户使用的 macintosh 可访问卷中的现有目录。 **Macfile 目录**命令不会创建目录。

- 使用**macfile directory**命令之前，请使用文件管理器、命令提示符或**macintosh 新文件夹**命令在 macintosh 可访问的卷中创建一个目录。

#### <a name="examples"></a>示例

若要分配 "*查看文件*"、"查看*文件夹*" 和 "对所有者*进行更改*" 权限，若要将 "*查看文件夹*权限" 设置为 "所有其他用户"，并防止目录被重命名、移动或删除，请键入：

```
macfile directory /path:e:\statistics\may sales /permissions:11111011000
```

其中，子目录*可以是 sales*，位于 E:\ 上 Macintosh 可访问的卷*统计信息*中本地服务器的驱动器。

## <a name="join-a-macintosh-files-data-and-resource-forks"></a>加入 Macintosh 文件的数据和资源分叉

指定要在其上联接文件的服务器、创建文件的用户、数据分叉所在的文件类型、资源分叉所在位置以及输出文件应位于的位置。

### <a name="syntax"></a>语法

```
macfile forkize[/server:\\<computername>] [/creator:<creatorname>] [/type:<typename>]  [/datafork:<filepath>] [/resourcefork:<filepath>] /targetfile:<filepath>
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /server:`\\<computername>` | 指定要在其上联接文件的服务器。 如果省略，则在本地计算机上执行该操作。 |
| 于是`<creatorname>` | 指定文件的创建者。 Macintosh 查找器使用 **/creator**命令行选项来确定创建该文件的应用程序。 |
| /type`<typename>` | 指定文件的类型。 Macintosh 查找器使用 **/type**命令行选项来确定应用程序中创建文件的文件类型。 |
| /datafork:`<filepath>` | 指定要联接的数据分叉的位置。 可以指定远程路径。 |
| /resourcefork:`<filepath>` | 指定要联接的资源分叉的位置。 可以指定远程路径。 |
| /targetfile`<filepath>` | 指定通过联接数据分叉和资源分叉创建的文件的位置，或指定要更改其类型或创建者的文件的位置。 文件必须位于指定服务器上。 此参数是必需的。 |
| /? | 在命令提示符下显示帮助。 |

##### <a name="remarks"></a>备注

- 如果提供的信息包含空格或特殊字符，请在文本两侧使用引号 (例如，" `<computer name>` " ) 。

#### <a name="examples"></a>示例

若要在 Macintosh 可访问的卷*D:\Release*上创建文件*tree_app* ，请使用资源分叉*C:\Cross\Mac\Appcode*，并使此新文件显示为 macintosh 客户端作为应用程序 (macintosh 应用程序使用 type *appl.exe*) ，并 (签名) 设置为*木兰*，请键入：

```
macfile forkize /resourcefork:c:\cross\mac\appcode /type:APPL /creator:MAGNOLIA /targetfile:D:\Release\tree_app
```

若要将文件创建者更改为*Microsoft Word 5.1*，请在 server * \\ ServerA*上的*D:\Word documents\Group 文件*中为 file *Word.txt*键入：

```
macfile forkize /server:\\ServerA /creator:MSWD /type:TEXT /targetfile:d:\Word documents\Group files\Word.txt
```

## <a name="change-the-sign-in-message-and-limit-sessions"></a>更改登录消息和限制会话

更改当用户登录到 Macintosh 服务器的文件服务器时显示的登录消息，并限制可同时使用 Macintosh 的文件和打印服务器的用户数量。

### <a name="syntax"></a>语法

```
macfile server [/server:\\<computername>] [/maxsessions:{number | unlimited}] [/loginmessage:<message>]
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- |------------ |
| /server:`\\<computername>` | 指定要在其上更改参数的服务器。 如果省略，则在本地计算机上执行该操作。 |
| maxsessions`{number | unlimited}` | 指定可以同时对 Macintosh 使用文件和打印服务器的用户的最大数量。 如果省略，则服务器的**maxsessions**设置保持不变。 |
| /loginmessage:`<message>` | 更改 Macintosh 用户在登录到 Macintosh 服务器的文件服务器时看到的消息。 登录消息的最大字符数为199。 如果省略，则服务器的**loginmessage**消息将保持不变。 若要删除现有的登录消息，请包含 **/loginmessage**参数，但将该*消息*变量留空。 |
| /? | 在命令提示符下显示帮助。 |

##### <a name="remarks"></a>备注

- 如果提供的信息包含空格或特殊字符，请在文本两侧使用引号 (例如，" `<computer name>` " ) 。

#### <a name="examples"></a>示例

若要将本地服务器上的 Macintosh 会话的允许文件和打印服务器的数目更改为5个会话，并添加登录消息 "在完成时注销来自 Macintosh 的服务器"，请键入：

```
macfile server /maxsessions:5 /loginmessage:Sign off from Server for Macintosh when you are finished
```

## <a name="add-change-or-remove-macintosh-accessible-volumes"></a>添加、更改或删除 Macintosh 可访问的卷

添加、更改或删除 Macintosh 可访问的卷。

### <a name="syntax"></a>语法

```
macfile volume {/add|/set} [/server:\\<computername>] /name:<volumename>/path:<directory>[/readonly:{true | false}] [/guestsallowed:{true | false}] [/password:<password>] [/maxusers:{<number>>|unlimited}]
macfile volume /remove[/server:\\<computername>] /name:<volumename>
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `{/add | /set}` | 在添加或更改 Macintosh 可访问的卷时是必需的。 添加或更改指定的卷。 |
| /server:`\\<computername>` | 指定要在其上添加、更改或删除卷的服务器。 如果省略，则在本地计算机上执行该操作。 |
| /name`<volumename>` | 必需。 指定要添加、更改或删除的卷名称。 |
| /path`<directory>` | 仅在添加卷时才是必需的。 指定要添加的卷的根目录的路径。 |
| 只读`{true | false}` | 指定用户是否可以更改卷中的文件。 使用**True**可指定用户不能更改卷中的文件。 使用**False**指定用户可以更改卷中的文件。 如果在添加卷时省略，则允许对文件进行更改。 如果在更改卷时省略，则卷的**readonly**设置将保持不变。 |
| /guestsallowed:`{true | false}` | 指定以来宾身份登录的用户是否可以使用该卷。 使用**True**可指定来宾可以使用该卷。 使用**False**指定来宾不能使用该卷。 如果在添加卷时省略，来宾可以使用该卷。 如果在更改卷时省略，则卷的**guestsallowed**设置保持不变。 |
| /password`<password>` | 指定访问卷所需的密码。 如果在添加卷时省略，则不会创建密码。 如果在更改卷时省略此密码，则密码将保持不变。 |
| /maxusers:`{<number>> | unlimited}` | 指定可以同时使用卷上的文件的最大用户数。 如果在添加卷时省略，则不限数量的用户可以使用该卷。 如果在更改卷时省略，则**maxusers**值保持不变。                                                 |
| /remove | 删除 Macintosh 可访问的卷时是必需的。 删除指定的卷。 |
| /? | 在命令提示符下显示帮助。 |

##### <a name="remarks"></a>备注

- 如果提供的信息包含空格或特殊字符，请在文本两侧使用引号 (例如，" `<computer name>` " ) 。

#### <a name="examples"></a>示例

若要在本地服务器上创建名为 "*美国市场营销统计信息*" 的卷，使用 E 驱动器中的 "*统计*信息" 目录，并指定来宾不能访问该卷，请键入：

```
macfile volume /add /name:US Marketing Statistics /guestsallowed:false /path:e:\Stats
```

若要将上面创建的卷更改为只读，需要输入密码，并将最大用户数设置为5，请键入：

```
macfile volume /set /name:US Marketing Statistics /readonly:true /password:saturn /maxusers:5
```

若要添加名为*横向设计*的卷，请在服务器* \\ 木兰*上使用电子驱动器中的*树*目录，并指定来宾可以访问该卷，请键入：

```
macfile volume /add /server:\\Magnolia /name:Landscape Design /path:e:\trees
```

若要删除本地服务器上名为 "*销售报表*" 的卷，请键入：

```
macfile volume /remove /name:Sales Reports
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
