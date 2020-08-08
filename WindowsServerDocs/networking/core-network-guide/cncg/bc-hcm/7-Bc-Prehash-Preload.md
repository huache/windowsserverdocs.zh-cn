---
title: 在托管缓存服务器上预哈希和预加载内容（可选）
description: 本指南说明如何在运行 Windows Server 2016 和 Windows 10 的计算机上以托管缓存模式部署 BranchCache
manager: brianlic
ms.topic: article
ms.assetid: 7e79c66a-8555-4d8e-8691-d6c37377aab4
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 45d84103f3b41b08beb207bee570b469a3caf3dc
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87964223"
---
# <a name="prehash-and-preload-content-on-the-hosted-cache-server-optional"></a>托管缓存服务器上的 Prehash 和预加载内容（ \( 可选）\)

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

你可以使用本部分中的过程来 prehash 内容服务器上的内容、将内容添加到数据包，然后在托管缓存服务器上预加载内容。

这些过程是可选的，因为你不需要在托管缓存服务器上 prehash 和预加载内容。

如果未预加载内容，则当客户端通过 WAN 连接下载数据时，数据会自动添加到托管缓存。

>[!IMPORTANT]
>尽管这些过程是可选的，但如果你决定在托管缓存服务器上 prehash 和预加载内容，则需要执行这两个过程。

- [为 Web 和文件内容创建内容服务器数据包 &#40;可选&#41;](8-Bc-Data-Packages.md)

- [导入托管缓存服务器上的数据包 &#40;可选&#41;](9-Bc-Import-Data.md)

若要继续学习本指南，请参阅[为 Web 和文件内容创建内容服务器数据包 &#40;可选&#41;](8-Bc-Data-Packages.md)。