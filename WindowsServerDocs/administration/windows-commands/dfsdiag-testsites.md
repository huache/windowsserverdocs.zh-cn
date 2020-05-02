---
title: dfsdiag TestSites
description: Dfsdiag TestSites 的参考主题，通过验证充当命名空间服务器或文件夹（链接）目标的服务器是否具有与所有域控制器相同的站点关联来检查 active directory 域服务（AD DS）站点的配置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68048699a812beac94fa121d6801da5f42e5393b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719557"
---
# <a name="dfsdiag-testsites"></a>dfsdiag TestSites

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过验证充当命名空间服务器或文件夹（链接）目标的服务器是否在所有域控制器上具有相同的站点关联来检查 active directory 域服务（AD DS）站点的配置。

## <a name="syntax"></a>语法  
  
```  
dfsdiag /TestSites </Machine:<server name>| /DFSpath:<namespace root or DFS folder> [/Recurse]> [/Full]  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|-------|--------|  
|\/计算机：<server name>|要在其上验证站点关联的服务器的名称。|  
|\/DFSpath:<namespace root or DFS folder>|命名空间根或分布式文件系统（DFS）文件夹（链接），其中包含要验证其站点关联的目标。|  
|\/Recurse|枚举并验证指定命名空间根目录下的所有文件夹目标的站点关联。|  
|\/达到|验证 AD DS 和服务器的注册表中是否包含相同的站点关联信息。|  
  
## <a name="examples"></a>示例  
  
```  
dfsdiag /TestSites /Machine:MyServer  
```  
 
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace1\Folder1 /Full  
```  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace2 /Recurse /Full  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   - [命令行语法项](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

