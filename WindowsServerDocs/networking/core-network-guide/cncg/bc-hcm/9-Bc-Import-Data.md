---
title: 在托管缓存服务器上导入数据包（可选）
description: 本指南说明如何在运行 Windows Server 2016 和 Windows 10 的计算机上以托管缓存模式部署 BranchCache
manager: brianlic
ms.topic: article
ms.assetid: d6159e91-f77c-42ec-9180-14bbb230ad17
ms.author: lizross
author: eross-msft
ms.openlocfilehash: f496182125fb288bd4e8b97a72389682f95fcc31
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87955964"
---
# <a name="import-data-packages-on-the-hosted-cache-server-optional"></a>在托管缓存服务器上导入数据包（ \( 可选）\)

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

您可以使用此过程在托管缓存服务器上导入数据包和预加载内容。

此过程是可选的，因为你不需要在托管缓存服务器上 prehash 和预加载内容。

如果未预先 \- 加载内容，则会自动将数据添加到托管缓存，因为客户端会通过 WAN 连接进行下载。

您必须是 Administrators 组的成员才能执行此过程。

## <a name="to-import-data-packages-on-the-hosted-cache-server"></a>导入托管缓存服务器上的数据包

1. 在服务器计算机上，打开具有管理员权限的 Windows PowerShell。

2. 键入以下命令，将– Path 参数的值替换为存储数据包的文件夹位置，然后按 ENTER。

    ```
    Import-BCCachePackage –Path D:\temp\PeerDistPackage.zip
    ```

3. 如果你有多个要预加载内容的托管缓存服务器，请在每个托管缓存服务器上执行此过程。

若要继续学习本指南，请参阅[配置客户端通过服务连接点自动托管缓存发现](10-Bc-Client-By-Scp.md)。
