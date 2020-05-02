---
title: dfsdiag TestDFSConfig
description: Dfsdiag TestDFSConfig 的参考主题，用于检查分布式文件系统（DFS）命名空间的配置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 057b0662fddb7148837be16380d190cdb37382c5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719590"
---
# <a name="dfsdiag-testdfsconfig"></a>dfsdiag TestDFSConfig

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过执行以下操作检查分布式文件系统（DFS）命名空间的配置：  
  
-   验证 DFS 命名空间服务是否正在运行，并且其启动类型在所有命名空间服务器上是否设置为自动。  
  
-   验证 DFS 注册表配置在命名空间服务器之间是否一致。  
  
-   验证运行 Windows Server 2008 或更高版本的群集命名空间服务器上的以下依赖项：  
  
    -   与网络名称资源的命名空间根资源相关。  
  
    -   IP 地址资源依赖于网络名称资源。  
  
    -   命名空间根资源依赖于物理磁盘资源。

## <a name="syntax"></a>语法  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:<namespace>  
```  
  
#### <a name="parameters"></a>参数  
  
|       参数       |               描述               |
|-----------------------|-----------------------------------------|
| /DFSRoot:`<namespace>` | 要诊断的命名空间（DFS 根目录）。 |
  
## <a name="examples"></a>示例  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   - [命令行语法项](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

