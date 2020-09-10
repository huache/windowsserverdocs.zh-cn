---
title: dfsdiag testdcs
description: Dfsdiag testdcs 命令的参考文章，用于检查指定域中的域控制器的配置。
ms.topic: reference
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0c2796cc149d905abae56bb909d337862c5fd7f2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633853"
---
# <a name="dfsdiag-testdcs"></a>dfsdiag testdcs

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过在指定域中的每个域控制器上执行以下测试来检查域控制器的配置：

- 验证分布式文件系统 (DFS) 命名空间服务是否正在运行，并且其启动类型是否已设置为 " **自动**"。

- 检查 NETLOGON 和 SYSvol 是否支持站点开销的引用。

- 验证站点关联的一致性（按主机名和 IP 地址）。

## <a name="syntax"></a>语法

```
dfsdiag /testdcs [/domain:<domain_name>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /domain`<domain_name>` | 要检查的域的名称。 此参数是可选的。 默认值为本地主机所联接到的本地域。 |

## <a name="examples"></a>示例

若要验证 *contoso.com* 域中的域控制器的配置，请键入：

```
dfsdiag /testdcs /domain:contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
