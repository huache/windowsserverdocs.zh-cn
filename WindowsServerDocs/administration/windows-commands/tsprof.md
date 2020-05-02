---
title: tsprof
description: Tsprof 的参考主题，它将远程桌面服务用户配置信息从一个用户复制到另一个用户。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5a4980455eb2901db949a06f0c6dfec9ecf5793
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721227"
---
# <a name="tsprof"></a>tsprof

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将远程桌面服务用户配置信息从一个用户复制到另一个用户。
远程桌面服务用户配置信息显示在 "本地用户和组" 和 "active directory 用户和计算机" 的远程桌面服务扩展中。

**tsprof**还可以设置用户的配置文件路径。



> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|/update|更新域 <*DomainName*> 中 <*用户名*> 的配置文件路径信息，以 <*Profilepath*>。|
|/domain：\<DomainName>|指定应用操作的域的名称。|
|/local|仅将操作应用于本地用户帐户。|
|/profile：\<路径>|指定在 "本地用户和组" 和 "active directory 用户和计算机" 的远程桌面服务扩展中显示的配置文件路径。|
|\<用户名>|指定要为其更新或查询服务器配置文件路径的用户的名称。|
|/copy|将用户配置信息从\< *SourceUser*> 复制\<*到 DestinationUser*> 并将\< *DestinationUser*> 的配置文件路径信息\<更新到*Profilepath*>。 \< *SourceUser*> 和\< *DestinationUser*> 必须是本地的，或者必须\<*位于域域名*> 中。|
|\<Src_usr>|指定要从中复制用户配置信息的用户的名称。|
|\<Dest_usr>|指定要向其复制用户配置信息的用户的名称。|
|/q|显示要为其查询服务器配置文件路径的用户的当前配置文件路径。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   仅当你在运行 windows server 2008 R2 的计算机上运行 Windows Server 2008 或 RD 会话主机角色服务的计算机上安装了终端服务器角色服务时， **tsprof**命令才可用。

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
- [命令行语法键](command-line-syntax-key.md)
[远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
