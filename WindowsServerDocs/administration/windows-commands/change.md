---
title: 更改
description: 用于更改的 Windows 命令主题，更改登录、COM 端口映射和安装模式远程桌面会话主机服务器设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90012116-0fb3-4f34-a819-cf4d4b4f8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5d91f8d0941fc96e776c761b9c7037e58588df8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847950"
---
# <a name="change"></a>更改

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改登录、COM 端口映射和安装模式远程桌面会话主机服务器设置。

> [!NOTE]
> 在 Windows Server 2008 R2 中，“终端服务”被重命名为“远程桌面服务”。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法

 ```
 change logon
 change port
 change user
 ```
 
 ### <a name="parameters"></a>参数
 
 |            参数            |                                                   说明                                                   |
 |---------------------------------|-----------------------------------------------------------------------------------------------------------------|
 | [change logon](change-logon.md) | 启用或禁用从 rd 会话主机服务器上的客户端会话登录，或显示当前登录状态。 |
 |  [change port](change-port.md)  |                列出或更改 COM 端口映射，使其与 MS-DOS 应用程序兼容。                |
 |  [change user](change-user.md)  |                            更改 rd 会话主机服务器的安装模式。                             |
 
 ## <a name="additional-references"></a>其他参考
 - [命令行语法键](command-line-syntax-key.md)
 [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
