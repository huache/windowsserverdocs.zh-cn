---
title: autochk
description: 用于在计算机启动时或在 Windows Server 开始验证文件系统的逻辑完整性之前运行的 autochk 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8787e6a3-f023-4ea5-b2d1-61c6876d8aff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cfb034f37f85b1e54e0cee2a8a4d128518c775a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923628"
---
# <a name="autochk"></a>autochk

在计算机启动时以及在 Windows Server 开始验证文件系统的逻辑完整性之前运行。

**Autochk.exe**是仅在 NTFS 磁盘上运行且仅在 Windows Server 启动之前运行的**chkdsk**版本。 不能从命令行直接运行**autochk** 。 而在下列情况下， **autochk**会运行：

- 如果尝试在启动卷上运行**chkdsk** 。

- 如果**chkdsk**无法获取卷的独占使用。

- 如果将卷标记为 "脏"。

## <a name="remarks"></a>备注

> [!WARNING]
> 不能从命令行直接运行**autochk**命令行工具。 请改用**chkntfs**命令行工具来配置在启动时要运行**autochk**的方式。
>
> - 可以将**chkntfs**与 **/x**参数一起使用，以防止**autochk**在特定卷或多个卷上运行。
>
> - 使用带有 **/t**参数的**chkntfs.exe**命令行工具将 autochk 延迟从0秒更改为最多3天（259200秒）。 不过，长时间延迟意味着计算机在超时或按下某个键以取消**autochk**之前，不会启动。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [chkdsk 命令](chkdsk.md)

- [chkntfs 命令](chkntfs.md)
