---
title: tsprof
description: Tsprof 的参考文章，可将远程桌面服务用户配置信息从一个用户复制到另一个用户。
ms.topic: reference
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: de1acc0c99f91f3ebf01d09d39d9fb0685d7f8f6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626697"
---
# <a name="tsprof"></a>tsprof

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将远程桌面服务用户配置信息从一个用户复制到另一个用户。
远程桌面服务用户配置信息显示在 "本地用户和组" 和 "active directory 用户和计算机" 的远程桌面服务扩展中。

**tsprof** 还可以设置用户的配置文件路径。

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的 [Windows server 2012 远程桌面服务中的新增功能](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11)) 。

## <a name="syntax"></a>语法
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/update|更新域 <*DomainName*> 中 <*用户名*> 的配置文件路径信息，以 <*Profilepath*>。|
|/domain\<DomainName>|指定应用操作的域的名称。|
|/local|仅将操作应用于本地用户帐户。|
|/profile\<path>|指定在 "本地用户和组" 和 "active directory 用户和计算机" 的远程桌面服务扩展中显示的配置文件路径。|
|\<UserName>|指定要为其更新或查询服务器配置文件路径的用户的名称。|
|/copy|将用户配置信息从复制 \<*SourceUser*> 到 \<*DestinationUser*> ，并将的配置文件路径信息更新为 \<*DestinationUser*> \<*Profilepath*> 。 \<*SourceUser*>和 \<*DestinationUser*> 必须都是本地的，或者必须在域中 \<*DomainName*> 。|
|\<Src_usr>|指定要从中复制用户配置信息的用户的名称。|
|\<Dest_usr>|指定要向其复制用户配置信息的用户的名称。|
|/q|显示要为其查询服务器配置文件路径的用户的当前配置文件路径。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   仅当你在运行 windows server 2008 R2 的计算机上运行 Windows Server 2008 或 RD 会话主机角色服务的计算机上安装了终端服务器角色服务时， **tsprof** 命令才可用。

## <a name="examples"></a>示例
-   若要将用户配置信息从 LocalUser1 复制到 LocalUser2，请键入：
    ```
    tsprof /copy /local LocalUser1 LocalUser2
    ```
-   若要将 LocalUser1 的远程桌面服务配置文件路径设置为名为 c:\profiles 的目录，请键入：
    ```
    tsprof /update /local /profile:c:\profiles LocalUser1
    ```

## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[远程桌面服务 (终端服务) 命令参考](remote-desktop-services-terminal-services-command-reference.md)
