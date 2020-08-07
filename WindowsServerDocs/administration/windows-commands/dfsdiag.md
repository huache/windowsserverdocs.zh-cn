---
title: dfsdiag
description: Dfsdiag 命令的参考文章，该命令提供 DFS 命名空间的诊断信息。
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ea349e088ccecd772130d30bfba01cbd1bf2e8e6
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891057"
---
# <a name="dfsdiag"></a>dfsdiag

提供 DFS 命名空间的诊断信息。

## <a name="syntax"></a>语法

```
dfsdiag /testdcs [/domain:<domain name>]
dfsdiag /testsites </machine:<server name>| /DFSPath:<namespace root or DFS folder> [/recurse]> [/full]
dfsdiag /testdfsconfig /DFSRoot:<namespace>
dfsdiag /testdfsintegrity /DFSRoot:<DFS root path> [/recurse] [/full]
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [dfsdiag testdcs](dfsdiag-testdcs.md) | 检查域控制器配置。 |
| [dfsdiag testsites](dfsdiag-testsites.md) | 检查站点关联。 |
| [dfsdiag testdfsconfig](dfsdiag-testdfsconfig.md) | 检查 DFS 命名空间配置。 |
| [dfsdiag testdfsintegrity](dfsdiag-testdfsintegrity.md) | 检查 DFS 命名空间的完整性。 |
| [dfsdiag testreferral](dfsdiag-testreferral.md) | 检查引用响应。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
