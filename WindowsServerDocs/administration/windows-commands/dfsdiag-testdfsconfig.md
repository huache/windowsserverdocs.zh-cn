---
title: dfsdiag testdfsconfig
description: 用于检查 (DFS) 命名空间的分布式文件系统配置的 dfsdiag testdfsconfig 参考文章。
ms.topic: reference
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60070b9f4076ee90cf0705992f31aff583f92968
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024001"
---
# <a name="dfsdiag-testdfsconfig"></a>dfsdiag testdfsconfig

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过执行以下操作，检查分布式文件系统 (DFS) 命名空间的配置：

- 验证 DFS 命名空间服务是否正在运行，并且其启动类型在所有命名空间服务器上是否设置为 **自动** 。

- 验证 DFS 注册表配置在命名空间服务器之间是否一致。

- 验证群集命名空间服务器上的以下依赖关系：

  - 与网络名称资源的命名空间根资源相关。

  - IP 地址资源依赖于网络名称资源。

  - 命名空间根资源依赖于物理磁盘资源。

## <a name="syntax"></a>语法

```
dfsdiag /testdfsconfig /DFSroot:<namespace>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /DFSroot:`<namespace>` | 命名空间 (要诊断的 DFS 根) 。 |

## <a name="examples"></a>示例

若要验证 *com\MyNamespace*中 (DFS) 命名空间的配置分布式文件系统，请键入：

```
dfsdiag /testdfsconfig /DFSroot:\contoso.com\MyNamespace
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
