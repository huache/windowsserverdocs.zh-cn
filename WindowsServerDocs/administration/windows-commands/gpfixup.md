---
title: gpfixup
description: Gpfixup 命令的参考文章，用于在域重命名操作后修复组策略对象中的域名依赖关系和组策略链接。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2b145410-fc75-4526-932d-f16b7ee3aaef
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c09efb2fc8b1de124cbefc1b2dff73df29d2a4f1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924650"
---
# <a name="gpfixup"></a>gpfixup

解决域重命名操作后组策略对象和组策略链接中的域名依赖关系。 若要使用此命令，必须通过服务器管理器将组策略管理作为一项功能安装。

## <a name="syntax"></a>语法

```
gpfixup [/v]
[/olddns:<olddnsname> /newdns:<newdnsname>]
[/oldnb:<oldflatname> /newnb:<newflatname>]
[/dc:<dcname>] [/sionly]
[/user:<username> [/pwd:{<password>|*}]] [/?]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| /v | 显示详细的状态消息。 如果未使用此参数，则只会显示错误消息或摘要状态消息，其中显示了 "**成功**" 或 "**失败**"。 |
| /olddns:`<olddnsname>` | 指定重命名域的旧 DNS 名称，就像 `<olddnsname>` 域重命名操作更改域的 DNS 名称一样。 仅当你还使用 **/newdns**参数来指定新的域 DNS 名称时，才能使用此参数。 |
| /newdns:`<newdnsname>` | 指定重命名域的新 DNS 名称，就像 `<newdnsname>` 域重命名操作更改域的 DNS 名称一样。 仅当你还使用 **/olddns**参数来指定旧的域 DNS 名称时，才能使用此参数。 |
| /oldnb:`<oldflatname>` | 指定重命名域的旧 NetBIOS 名称，就像 `<oldflatname>` 域重命名操作更改域的 NetBIOS 名称一样。 仅当使用 **/newnb**参数指定新的域 NetBIOS 名称时，才能使用此参数。 |
| /newnb:`<newflatname>` | 指定重命名域的新 NetBIOS 名称，就像 `<newflatname>` 域重命名操作更改域的 netbios 名称一样。 仅当使用 **/oldnb**参数指定旧的域 NetBIOS 名称时，才能使用此参数。 |
| /dc`<dcname>` | 连接到名为的域控制器 `<dcname>` （DNS 名称或 NetBIOS 名称）。 `<dcname>`必须承载域目录分区的可写副本，如下所示：<ul><li>`<newdnsname>`使用 **/NEWDNS**的 DNS 名称</li><li>`<newflatname>`使用 **/Newnb**的 NetBIOS 名称</br>如果未使用此参数，则可以连接到或所指示的重命名域中的任何域控制器 `<newdnsname>` `<newflatname>` 。</li></ul> |
| /sionly | 仅执行与托管软件安装相关的组策略修补程序（组策略的软件安装扩展）。 跳过修复组策略链接和 Gpo 中 SYSVOL 路径的操作。 |
| /user`<username>` |在用户的安全上下文中运行此命令 `<username>` ，其中 `<username>` 的格式为 domain\user 如果未使用此参数，则此命令以登录用户的身份运行。 |
| /pwd`{<password> | *}` | 指定用户的密码。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

此示例假设你已执行域重命名操作，其中你将 DNS 名称从**MyOldDnsName**更改为**MyNewDnsName**，并将 NetBIOS 名称从**MyOldNetBIOSName**更改为**MyNewNetBIOSName**。

在此示例中，使用**gpfixup**命令连接到名为**MyDcDnsName**的域控制器，并通过更新在 gpo 和链接中嵌入的旧域名来修复 gpo 和组策略链接。 状态和错误输出保存到名为**gpfixup**的文件中。

```
gpfixup /olddns: MyOldDnsName /newdns:MyNewDnsName /oldnb:MyOldNetBIOSName /newnb:MyNewNetBIOSName /dc:MyDcDnsName 2>&1 >gpfixup.log
```

此示例与上一个示例相同，不同之处在于它假定域的 NetBIOS 名称在域重命名操作过程中未更改。

```
gpfixup /olddns: MyOldDnsName /newdns:MyNewDnsName /dc:MyDcDnsName 2>&1 >gpfixup.log
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [管理 Active Directory 域重命名](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794869(v=ws.10))
