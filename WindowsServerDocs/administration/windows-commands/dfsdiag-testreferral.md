---
title: dfsdiag testreferral
description: Dfsdiag testreferral 命令的参考主题，用于检查分布式文件系统（DFS）引用。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 23abcd738170d5f53e12ae83c41d632d2d7ac738
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992927"
---
# <a name="dfsdiag-testreferral"></a>dfsdiag testreferral

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过执行以下测试检查分布式文件系统（DFS）引用：

- 如果使用不带参数的**DFSpath*** 参数，则该命令将验证引用列表是否包含所有受信任的域。

- 如果指定域，则该命令将执行域控制器（`dfsdiag /testdcs`）的运行状况检查，并测试本地主机的站点关联和域缓存。

- 如果指定域和 \SYSvol 或 \NETLOGON，则该命令将执行相同的域控制器运行状况检查，并检查 SYSvol 或 NETLOGON 引用的**生存时间（TTL）** 是否与默认值900秒匹配。

- 如果指定命名空间根，则该命令将执行相同的域控制器运行状况检查，以及执行 DFS 配置检查（`dfsdiag /testdfsconfig`）和命名空间完整性检查（`dfsdiag /testdfsintegrity`）。

- 如果指定 DFS 文件夹（链接），该命令将执行相同的命名空间根运行状况检查，并验证文件夹目标（dfsdiag/testsites）的站点配置并验证本地主机的站点关联。

## <a name="syntax"></a>语法

```
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /DFSpath:`<path to get referrals>` | 可以是以下值之一：<ul><li>**空白：** 仅测试受信任的域。</li><li>`\\Domain:`仅测试域控制器的引用。</li><li>`\\Domain\SYSvol:`仅测试 SYSvol 引用。</li><li>`\\Domain\NETLOGON:`仅测试 NETLOGON 引用。</li><li>`\\<domain or server>\<namespace root>:`仅测试命名空间根引用。</li><li>`\\<domain or server>\<namespace root>\<DFS folder>:`仅测试 DFS 文件夹（链接）引用。</li></ul> |
| /full | 仅适用于域和根引用。 验证注册表和 active directory 域服务（AD DS）之间的站点关联信息一致性。 |

## <a name="examples"></a>示例

若要检查*com\MyNamespace*中的分布式文件系统（DFS）引用，请键入：

```
dfsdiag /testreferral /DFSpath:\\contoso.com\MyNamespace
```

若要检查所有受信任域中的分布式文件系统（DFS）引用，请键入：

```
dfsdiag /testreferral /DFSpath:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
