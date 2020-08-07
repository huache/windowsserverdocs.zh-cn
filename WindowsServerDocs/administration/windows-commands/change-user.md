---
title: change user
description: 更改用户命令的参考文章，用于更改远程桌面会话主机服务器的安装模式。
ms.topic: article
ms.assetid: 6202f024-8cf5-411e-89b1-ee37ff46499d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca78126095b11ca7bf900d10c253cd7ad19fcc12
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892900"
---
# <a name="change-user"></a>change user

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改远程桌面会话主机服务器的安装模式。

> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅[Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
change user {/execute | /install | /query}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| / execute | 使.ini 文件映射到主目录。 这是默认设置。 |
| /install | 禁用.ini 文件映射到主目录。 所有的.ini 文件读取并写入到系统目录中。 在远程桌面会话主机服务器上安装应用程序时，必须禁用 .ini 文件映射。 |
| /query | 显示当前设置的.ini 文件映射。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 使用 **更改 user /install** 之前安装的应用程序在系统目录中创建的应用程序的.ini 文件。 创建特定于用户的.ini 文件时，这些文件使用作为源。 安装后该应用程序，使用 **更改用户 / execute** ，将恢复为标准.ini 文件映射。

- 首次运行应用时，它将在主目录中搜索其 .ini 文件。 如果在主目录中找不到 .ini 文件，但在系统目录中找到该文件，远程桌面服务将 .ini 文件复制到主目录，确保每个用户都具有应用程序 .ini 文件的唯一副本。 主目录中创建任何新的.ini 文件。

- 每个用户应具有应用程序的.ini 文件的唯一副本。 这可以防止不同用户可能有不兼容的应用程序配置 （例如，不同的默认目录或屏幕分辨率）。

- 当系统正在运行时，**更改用户/install**，会发生多种情况。 所有创建的注册表项都将在**\SOFTWARE**子项或**\MACHINE**子项中**HKEY_LOCAL_MACHINE \software\microsoft\windows NT\Currentversion\Terminal Server\Install**下隐藏。 子项添加到 **HKEY_CURRENT_USER** 将复制到下方 **\SOFTWARE** 子项，并且子项添加到 **HKEY_LOCAL_MACHINE** 将复制到下方 **\MACHINE** 子项。 如果应用程序使用系统调用（如 GetWindowsdirectory）查询 Windows 目录，则 rd 会话主机服务器会返回 systemroot 目录。 如果使用的系统调用，如 WritePrivateProfileString，添加了任何.ini 文件条目添加到 systemroot 目录下的.ini 文件。

- 当系统返回**更改用户/execute**，并且应用程序尝试读取**HKEY_CURRENT_USER**中不存在的注册表项时，远程桌面服务检查是否存在该密钥的副本是否存在于**\Terminal Server\Install**子项下。 如果已存在，则子项被复制到下的适当位置 **HKEY_CURRENT_USER**。 如果应用程序尝试读取.ini 文件不存在，远程桌面服务会搜索该.ini 文件系统根目录下。 如果.ini 文件系统根目录中，该证书复制到用户的主目录的 \Windows 子目录。 如果应用程序查询 Windows 目录，则 rd 会话主机服务器将返回用户的主目录的 \Windows 子目录。

- 当您登录时，远程桌面服务检查其系统.ini 文件是否比您的计算机上的.ini 文件。 如果系统版本较新，您的.ini 文件替换或者合并在一起的较新版本。 这取决于 INISYNC 类型为 bit，0x40，是为此.ini 文件设置。 以前版本的.ini 文件会重命名为 Inifile.ctx。 如果系统注册表值下 **\Terminal Server\Install** 子项的下您版本比新 **HKEY_CURRENT_USER**, ，您则子项的版本被删除并替换为新子项 **\Terminal Server\Install**。

## <a name="examples"></a>示例

- 若要禁用对主目录中的.ini 文件映射，请键入︰

  ```
  change user /install
  ```

- 若要启用对主目录中的.ini 文件映射，请键入︰

  ```
  change user /execute
  ```

- 若要显示.ini 文件映射的当前设置，请键入︰

  ```
  change user /query
  ```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [change 命令](change.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
