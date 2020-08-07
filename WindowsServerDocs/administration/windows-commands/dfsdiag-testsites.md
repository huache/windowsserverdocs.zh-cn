---
title: dfsdiag testsites
description: Dfsdiag testsites 参考文章，通过验证充当命名空间服务器或文件夹 (链接) 目标的服务器是否在所有域控制器上都具有相同的站点关联来检查 active directory 域服务 (AD DS) 站点的配置。
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d40d7833cabb9e03875660c7d4ebbc129eff0255
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891119"
---
# <a name="dfsdiag-testsites"></a>dfsdiag testsites

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过验证充当命名空间服务器或文件夹 (链接) 目标的服务器是否在所有域控制器上都具有相同的站点关联来检查 active directory 域服务 (AD DS) 站点的配置。

## <a name="syntax"></a>语法

```
dfsdiag /testsites </machine:<server name>| /DFSpath:<namespace root or DFS folder> [/recurse]> [/full]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `/machine:<server name>` | 要在其上验证站点关联的服务器的名称。 |
| `/DFSpath:<namespace root or DFS folder>` | 命名空间 root 或分布式文件系统 (DFS) 文件夹 (与要验证其站点关联的目标) 链接。 |
| /recurse | 枚举并验证指定命名空间根目录下的所有文件夹目标的站点关联。 |
| /full | 验证 AD DS 和服务器的注册表中是否包含相同的站点关联信息。 |

## <a name="examples"></a>示例

若要检查*machine\MyServer*上的站点关联，请键入：

```
dfsdiag /testsites /machine:MyServer
```

若要检查分布式文件系统 (DFS) 文件夹来验证站点关联，同时验证服务器的 AD DS 和注册表是否包含相同的站点关联信息，请键入：

```
dfsdiag /TestSites /DFSpath:\\contoso.com\namespace1\folder1 /full
```

若要检查命名空间根目录以验证站点关联，同时为指定的命名空间根目录下的所有文件夹目标枚举并验证站点关联，并验证 AD DS 和服务器的注册表是否包含相同的站点关联信息，请键入：

```
dfsdiag /testsites /DFSpath:\\contoso.com\namespace2 /recurse /full
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [dfsdiag 命令](dfsdiag.md)
