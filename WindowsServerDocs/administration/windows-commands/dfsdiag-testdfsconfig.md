---
title: dfsdiag testdfsconfig
description: Dfsdiag testdfsconfig 的参考主题，用于检查分布式文件系统（DFS）命名空间的配置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d9490f35c2d509c83d9008aa87627bd3c55a875
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992986"
---
# <a name="dfsdiag-testdfsconfig"></a>dfsdiag testdfsconfig

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过执行以下操作检查分布式文件系统（DFS）命名空间的配置：

- 验证 DFS 命名空间服务是否正在运行，并且其启动类型在所有命名空间服务器上是否设置为**自动**。

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
| /DFSroot:`<namespace>` | 要诊断的命名空间（DFS 根目录）。 |

## <a name="examples"></a>示例

若要验证*com\MyNamespace*中的分布式文件系统（DFS）命名空间的配置，请键入：

```
dfsdiag /testdfsconfig /DFSroot:\contoso.com\MyNamespace
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
