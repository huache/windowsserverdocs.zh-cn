---
title: dfsutil
description: 用于 dfsutil 的 Windows 命令主题，用于管理 DFS 命名空间、服务器和客户端。 dfsutil 命令使用原始分布式文件系统术语，其中包含已更新的 DFS 命名空间术语，作为对大多数命令的说明。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef5093a4-0d24-4b21-9d04-59933ad98e2c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30415bc85fd8a4a4804946a3d4a168d6a7d1433a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845580"
---
# <a name="dfsutil"></a>dfsutil

>适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Dfsutil 命令管理 DFS 命名空间、服务器和客户端。 在大多数情况下，你可以改用较新的 DFS 命名空间 PowerShell cmdlet，尽管有几个命令仍需要 dfsutil。

## <a name="parameters-available-in-powershell"></a>PowerShell 中的可用参数

可以通过 PowerShell 使用以下参数：

| 参数 | 说明 |
| --------- | ----------- |
| root | 显示、创建、删除、导入、导出命名空间根目录。 |
| link | 显示、创建、删除或移动文件夹（链接）。 |
| target | 显示、创建、删除文件夹目标或命名空间服务器。 |
| property | 显示或修改文件夹目标或命名空间服务器。 |
| server | 显示或修改命名空间配置。 |
| domain | 显示域中基于域的所有命名空间。 |

## <a name="parameters-only-available-in-dfsutil"></a>仅在 dfsutil 中提供参数

只能从 dfsutil 使用以下参数。

| 参数 | 说明 |
| --------- | ----------- |
| 客户端 | 显示或修改客户端信息或注册表项。 |
| 斜 | 执行诊断或查看 dfsdirs/dfspath。 |
| 缓存 | 显示或刷新客户端缓存。 |

有关这些命令的详细信息，请在安装了 DFS 命名空间管理工具的服务器上打开命令提示符，然后键入 `dfsutil client /?`、`dfsutil diag /?`或 `dfsutil cache /?`。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)