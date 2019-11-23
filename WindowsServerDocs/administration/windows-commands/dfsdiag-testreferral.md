---
title: dfsdiag TestReferral
description: '适用于 * * * * 的 Windows 命令主题 '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af22520d2c89f9d9f9d91ea6f43a33f3ff9c57f1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378358"
---
# <a name="dfsdiag-testreferral"></a>dfsdiag TestReferral

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

通过执行以下测试来检查分布式文件系统 \(DFS\) 引用：  
  
-   使用不带参数的 DFSpath 参数时，此命令将验证引用列表是否包含所有受信任的域。  
  
-   指定域时，该命令将对域控制器 \(dfsdiag \/testdcs\) 执行运行状况检查，并测试本地主机的站点关联和域缓存。  
  
-   指定域并 \\SYSvol 或 \\NETLOGON 时，除了执行指定域时相同的健康检查，该命令还会检查 SYSvol 或 NETLOGON 引用的生存时间 \(TTL\) 是否与默认值900秒匹配。  
  
-   当指定命名空间根时，除了执行指定域相同的运行状况检查外，此命令还会执行 DFS 配置检查 \(dfsdiag \/TestDFSConfig\) 和命名空间完整性检查 \(dfsdiag \/TestDFSIntegrity\)。  
  
-   当指定 \(link\)的 DFS 文件夹时，除了执行指定命名空间根时相同的健康检查，该命令还将验证文件夹目标的站点配置 \(dfsdiag \/testsites\) 并验证本地主机的站点关联。  
  
  
  
## <a name="syntax"></a>语法  
  
```  
dfsdiag /TestReferral /DFSpath:<DFS path for getting referrals> [/Full]  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|-------|--------|  
|\/DFSpath：<path for getting referrals>|此 DFS 路径可以是以下项之一：<br /><br />-   \(空白\)：测试受信任的域。<br />\\域 \\-   ：域控制器的引用。<br />-   \\\\域\\SYSvol： SYSvol 引用。<br />-   \\\\域\\NETLOGON： NETLOGON 引用。<br />-   \\\\<Domain or server>\\<Namespace Root>：命名空间根路径引用。<br />-   \\\\<Domain or server>\\<Namespace root>\\<DFS folder>： DFS 文件夹 \(链接\) 引用。|  
|\/Full|仅适用于域和根引用。 验证注册表和 active directory 域服务之间的站点关联信息的一致性 \(AD DS\)。|  
  
## <a name="BKMK_Examples"></a>示例  
若要待定，请键入：  
  
```  
dfsdiag /TestReferral /DFSpath:\\Contoso.com\MyNamespace  
```  
  
若要待定，请键入：  
  
```  
dfsdiag /TestReferral /DFSpath:  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   [命令行语法项](command-line-syntax-key.md)  
  

