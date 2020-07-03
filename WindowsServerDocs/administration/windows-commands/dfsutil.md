---
title: dfsutil
description: 用于管理 DFS 命名空间、服务器和客户端的 dfsutil 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef5093a4-0d24-4b21-9d04-59933ad98e2c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c741635b2566a7bec7775de691105c15591caa62
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930609"
---
# <a name="dfsutil"></a>dfsutil

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Dfsutil 命令管理 DFS 命名空间、服务器和客户端。

## <a name="functionality-available-in-powershell"></a>PowerShell 中的可用功能

[DFSN](https://docs.microsoft.com/powershell/module/dfsn/?view=win10-ps) PowerShell 模块为以下 dfsutil 参数提供等效功能。

| 参数 | 说明 |
| --------- | ----------- |
| root | 显示、创建、删除、导入、导出命名空间根目录。 |
| 链接 | 显示、创建、删除或移动文件夹（链接）。 |
| 目标 | 显示、创建、删除文件夹目标或命名空间服务器。 |
| property | 显示或修改文件夹目标或命名空间服务器。 |
| server | 显示或修改命名空间配置。 |
| 域 | 显示域中基于域的所有命名空间。 |

## <a name="functionality-available-only-in-dfsutil"></a>仅在 dfsutil 中可用的功能

以下功能仅作为 dfsutil 参数提供：

| 参数 | 说明 |
| --------- | ----------- |
| 客户端 | 显示或修改客户端信息或注册表项。 |
| 斜 | 执行诊断或查看 dfsdirs/dfspath。 |
| cache | 显示或刷新客户端缓存。 |

有关这些命令的详细信息，请在安装了 DFS 命名空间管理工具的服务器上打开命令提示符，然后键入 `dfsutil client /?` 、 `dfsutil diag /?` 或 `dfsutil cache /?` 。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)