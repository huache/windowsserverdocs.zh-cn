---
title: tlntadmn
description: 用于管理本地或远程计算机（运行 telnet 服务器服务）的 tlntadmn.exe 参考文章。
ms.topic: article
ms.assetid: 78b61e8d-b953-44bb-8d57-f3b42da9e7a8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4dee63c0233bab5341dae724ccd9779c3917054c
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87897142"
---
# <a name="tlntadmn"></a>tlntadmn

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

管理运行 telnet 服务器服务的本地或远程计算机。

## <a name="syntax"></a>语法
```
tlntadmn [<computerName>] [-u <UserName>] [-p <Password>] [{start | stop | pause | continue}] [-s {<SessionID> | all}] [-k {<SessionID> | all}] [-m {<SessionID> | all}  <Message>] [config [dom = <Domain>] [ctrlakeymap = {yes | no}] [timeout = <hh>:<mm>:<ss>] [timeoutactive = {yes | no}] [maxfail = <attempts>] [maxconn = <Connections>] [port = <Number>] [sec {+ | -}NTLM {+ | -}passwd] [mode = {console | stream}]] [-?]
```
#### <a name="parameters"></a>参数

|                   参数                    |                                                                                                                                                       描述                                                                                                                                                        |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                \<computerName>                 |                                                                                                                    指定要连接到的服务器的名称。 默认为本地计算机。                                                                                                                    |
|         -u \<UserName> -p\<Password>          |                                                指定要管理的远程服务器的管理凭据。 如果要管理未使用管理凭据登录的远程服务器，则此参数是必需的。                                                |
|                     start                      |                                                                                                                                            启动 telnet 服务器服务。                                                                                                                                             |
|                      stop                      |                                                                                                                                             停止 telnet 服务器服务                                                                                                                                              |
|                     pause                      |                                                                                                                          暂停 telnet 服务器服务。 不会接受任何新连接。                                                                                                                          |
|                    continue                    |                                                                                                                                            恢复 telnet 服务器服务。                                                                                                                                            |
|          -s { \<SessionID> 全部 &#124;}          |                                                                                                                                             显示活动的 telnet 会话。                                                                                                                                             |
|          -k { \<SessionID> 全部 &#124;}          |                                                                                                        结束 telnet 会话。 键入用于结束特定会话的会话 ID，或键入 all 结束所有会话。                                                                                                         |
|    -m { \<SessionID> 全部 &#124;}<Message>     |                                                   将消息发送到一个或多个会话。 键入用于将消息发送到特定会话的会话 ID，或键入 all 以便向所有会话发送消息。 键入要在引号之间发送的消息。                                                   |
|             配置 dom =\<Domain>             |                                                                                                                                      配置服务器的默认域。                                                                                                                                       |
|      config ctrlakeymap = {yes &#124; no}      |                                                                                     指定是否希望 telnet 服务器将 CTRL + A 解释为 ALT。 键入 **"是"** 以映射快捷键，或键入 "**否**" 以阻止映射。                                                                                     |
|       配置超时 = \<hh> ： \<mm>\<ss>       |                                                                                                                                 以小时、分钟和秒为单位设置超时期限。                                                                                                                                 |
|     config timeoutactive = {yes &#124; no      |                                                                                                                                            启用空闲会话超时。                                                                                                                                             |
|          config maxfail =\<attempts>          |                                                                                                                          设置在断开连接前失败的最大登录尝试次数。                                                                                                                          |
|        config maxconn =\<Connections>         |                                                                                                                                         设置最大连接数。                                                                                                                                          |
|            config port = < \Number of>             |                                                                                                                    设置 telnet 端口。 必须使用小于1024的整数指定端口。                                                                                                                    |
| config sec {+ &#124;-} NTLM {+ &#124;-} 密码 | 指定是否要使用 NTLM 和/或密码对登录尝试进行身份验证。 若要使用特定类型的身份验证，请在 **+** 该类型的身份验证之前键入一个加号 () 。 若要防止使用特定类型的身份验证，请在 **-** 该类型的身份验证之前键入减号 () 。 |
|     配置模式 = {控制台 &#124; 流}      |                                                                                                                                             指定操作模式。                                                                                                                                             |
|                       -?                       |                                                                                                                                           在命令提示符下显示帮助。                                                                                                                                           |

## <a name="remarks"></a>备注
-   若要显示服务器设置，请键入不带任何参数的**tlntadmn.exe** 。
-   若要使用**tlntadmn.exe**命令，必须使用管理凭据登录到本地计算机。 若要管理远程计算机，还必须为远程计算机提供管理凭据。 为此，可以登录到本地计算机，该帐户具有本地计算机和远程计算机的管理凭据。 如果无法使用此方法，则可以使用 **-u**和 **-p**参数为远程计算机提供管理凭据。

## <a name="examples"></a>示例
将空闲会话超时配置为30分钟。
```
tlntadmn config timeout=0:30:0
```
显示活动的 telnet 会话。
```
tlntadmn -s
```

## <a name="additional-references"></a>其他参考
-   [telnet 操作指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753164(v=ws.10))
- [命令行语法项](command-line-syntax-key.md)
