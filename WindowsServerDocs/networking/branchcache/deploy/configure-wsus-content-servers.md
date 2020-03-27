---
title: 配置 Windows Server Update Services (WSUS) 内容服务器
description: 本主题是适用于 Windows Server 2016 的 BranchCache 部署指南的一部分，它演示了如何在分布式缓存模式和托管缓存模式下部署 BranchCache，以优化分支机构中的 WAN 带宽使用。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9724aa8d-e4ae-404c-bee6-cef1534cd3ca
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 2993c78e85609ac720fd208971dda7ed67a3610d
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319166"
---
# <a name="configure-windows-server-update-services-wsus-content-servers"></a>配置 Windows Server Update Services (WSUS) 内容服务器

>适用于：Windows Server（半年频道）、Windows Server 2016

安装 BranchCache 功能并启动 BranchCache 服务后，必须将 WSUS 服务器配置为将更新文件存储在本地计算机上。 

当你将 WSUS 服务器配置为将更新文件存储在本地计算机上时，会下载更新元数据和更新文件并直接将它们存储在 WSUS 服务器上。 这可确保 BranchCache 客户端计算机从 WSUS 服务器接收 Microsoft 产品更新文件，而不是直接从 Microsoft 更新网站接收。  
  
有关 WSUS 同步的详细信息，请参阅[设置更新同步](https://technet.microsoft.com/library/mt612311.aspx)  