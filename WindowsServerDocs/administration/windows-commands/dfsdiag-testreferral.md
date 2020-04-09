---
title: dfsdiag TestReferral
description: 适用于 dfsdiag TestReferral 的 Windows 命令主题，用于检查分布式文件系统（DFS）引用。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5c0a75d557d816ac9e19a1e22b3273195b93f53
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846241"
---
# <a name="dfsdiag-testreferral"></a>dfsdiag TestReferral

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

通过执行以下测试检查分布式文件系统（DFS）引用：

- 使用不带参数的 DFSpath 参数时，此命令将验证引用列表是否包含所有受信任的域。

- 指定域时，该命令将执行域控制器（dfsdiag/testdcs）的运行状况检查，并测试本地主机的站点关联和域缓存。

- 指定域和 \SYSvol 或 \NETLOGON 时，除了执行指定域相同的健康检查以外，命令还会检查 SYSvol 或 NETLOGON 引用的生存时间（\TTL）是否与默认值900秒匹配。

- 当指定命名空间根时，除了执行指定域相同的运行状况检查外，此命令还执行 DFS 配置检查（dfsdiag/TestDFSConfig）和命名空间完整性检查（dfsdiag/TestDFSIntegrity）。

- 指定一个 DFS 文件夹（链接）时，除了执行与指定命名空间根时相同的健康检查外，此命令还将验证文件夹目标（dfsdiag/testsites）的站点配置，并验证本地主机的站点关联。

## <a name="syntax"></a>语法

```
dfsdiag /TestReferral /DFSpath:<DFS path for getting referrals> [/Full]
```

#### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
| /DFSpath：<path for getting referrals>|此 DFS 路径可以是以下项之一：<p>-   \(空白\)：测试受信任的域。<br />\\域 \\-   ：域控制器的引用。<br />-   \\\\域\\SYSvol： SYSvol 引用。<br />\\NETLOGON 中的 -   \\\\域名： NETLOGON 引用。<br />-   \\\\<Domain or server>\\<Namespace Root>：命名空间根路径引用。<br />-   \\\\<Domain or server>\\<Namespace root>\\<DFS folder>： DFS 文件夹 \(链接\) 引用。|
|/Full|仅适用于域和根引用。 验证注册表和 active directory 域服务之间的站点关联信息的一致性 \(AD DS\)。|

## <a name="examples"></a><a name=BKMK_Examples></a>示例

```
dfsdiag /TestReferral /DFSpath:\\Contoso.com\MyNamespace
```

```
dfsdiag /TestReferral /DFSpath:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)


