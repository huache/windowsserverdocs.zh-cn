---
title: dfsdiag
description: Dfsdiag 的参考主题，它提供 DFS 命名空间的诊断信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d5a9b147994628ccad6a723311decbccbe82ec6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719544"
---
# <a name="dfsdiag"></a>dfsdiag

提供 DFS 命名空间的诊断信息。

## <a name="syntax"></a>语法

```
dfsdiag [ /TestDCs [/Domain:<Domain name>]| /TestSites </Machine:<server name>| /DFSPath:<namespace root or DFS folder> [/Recurse]> [/Full] | /TestDFSConfig /DFSRoot:<namespace> | /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full] | /TestReferral /DFSPath:<DFS path for getting referrals> [/Full] | /?] 

```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[Dfsdiag TestDCs](dfsdiag-testdcs.md)|检查域控制器配置。|
|[Dfsdiag TestSites](dfsdiag-testsites.md)|检查站点关联。|
|[Dfsdiag TestDFSConfig](dfsdiag-testdfsconfig.md)|检查 DFS 命名空间配置。|
|[Dfsdiag TestDFSIntegrity](dfsdiag-testdfsintegrity.md)|检查 DFS 命名空间的完整性。|
|[Dfsdiag TestReferral](dfsdiag-testreferral.md)|检查引用响应。|
|/?|在命令提示符下显示帮助。|

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)