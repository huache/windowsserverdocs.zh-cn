---
title: query user
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a670fb78-c055-464a-b61d-3a85632c52c5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8c095226a5445e976e47e461044ec002dc007fe
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722693"
---
# <a name="query-user"></a>query user

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程桌面会话主机（rd 会话主机）服务器上的用户会话的相关信息。

> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。
> ## <a name="syntax"></a>语法
> ```
> query user [<UserName> | <SessionName> | <SessionID>] [/server:<ServerName>]
> ```
> ### <a name="parameters"></a>参数
> 
> |      参数       |                                                     描述                                                     |
> |----------------------|---------------------------------------------------------------------------------------------------------------------|
> |      <UserName>      |                            指定要查询的用户的登录名。                             |
> |    <SessionName>     |                              指定要查询的会话的名称。                              |
> |     <SessionID>      |                               指定要查询的会话的 ID。                               |
> | /server:<ServerName> | 指定要查询的 rd 会话主机服务器。 否则，使用当前的 rd 会话主机服务器。 |
> |          /?          |                                        在命令提示符下显示帮助。                                         |
> 
> ## <a name="remarks"></a>备注
> - 可以使用此命令查明特定用户是否已登录到特定的 rd 会话主机服务器。 **查询用户**返回以下信息：
>   -   用户的名称
>   -   Rd 会话主机服务器上的会话名称
>   -   会话 ID
>   -   会话的状态（活动或已断开连接）
>   -   空闲时间（自上一次击键或鼠标移动后的分钟数）
>   -   用户登录的日期和时间
> - 若要使用**查询用户**，您必须拥有 "完全控制" 权限或 "查询信息" 特殊访问权限。
> - 如果使用**查询用户**而不指定 <*用户名*>、<*会话*名称> 或 <*SessionID*>，则返回登录到服务器的所有用户的列表。 此外，还可以使用**查询会话**来显示服务器上所有会话的列表。
> - 当**查询用户**返回信息时，将在当前会话之前显示大于号（>）。
> - 仅当使用远程服务器上的**查询用户**时， **/server**参数才是必需的。
>   ## <a name="examples"></a>示例
> - 若要显示有关记录在系统上的所有用户的信息，请键入：
>   ```
>   query user
>   ```
> - 若要显示有关服务器 SERver1 上的用户 USER1 的信息，请键入：
>   ```
>   query user USER1 /server:SERver1
>   ```
>   ## <a name="additional-references"></a>其他参考
>   - [命令行语法关键字](command-line-syntax-key.md)
>   [查询](query.md)
>   [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
