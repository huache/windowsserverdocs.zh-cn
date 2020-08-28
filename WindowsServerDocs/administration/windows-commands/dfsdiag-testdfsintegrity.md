---
title: dfsdiag testdfsintegrity
description: 用于检查分布式文件系统 (DFS) 命名空间的完整性的 dfsdiag testdfsintegrity 命令的参考文章。
ms.topic: reference
ms.assetid: 173ee832-26e1-4ec8-a23a-38a7d6229ac3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7bcfbe7f35965322a347651133a90e6806a5bb95
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028415"
---
# <a name="dfsdiag-testdfsintegrity"></a>dfsdiag testdfsintegrity

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过执行以下测试来检查分布式文件系统 (DFS) 命名空间的完整性：

- 检查 DFS 元数据是否已损坏或域控制器之间存在不一致。

- 验证基于访问权限的枚举的配置，以确保 DFS 元数据和命名空间服务器共享之间的一致性。

- 检测与重叠文件夹目标) 、重复文件夹和文件夹 (链接的重叠 DFS 文件夹。

## <a name="syntax"></a>语法

```
dfsdiag /testdfsintegrity /DFSroot: <DFS root path> [/recurse] [/full]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /DFSroot: `<DFS root path>` | 要诊断的 DFS 命名空间。 |
| /recurse | 执行测试，包括任何命名空间 interlinks。 |
| /full | 验证共享和 NTFS Acl 的一致性，以及所有文件夹目标上的客户端配置。 它还会验证是否已设置联机属性。 |

## <a name="examples"></a>示例

若要验证 *com\MyNamespace*中 (DFS) 命名空间的完整性和分布式文件系统一致性（包括任何 interlinks），请键入：

```
dfsdiag /testdfsintegrity /DFSRoot:\contoso.com\MyNamespace /recurse /full
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
