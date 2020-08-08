---
title: 排查缓存和内存管理器性能问题
description: 排查 Windows Server 16 上的缓存和内存管理器性能问题
ms.topic: article
ms.author: pavel; atales
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: ba6c04ca8ac1941221809af958a9d6c53701b101
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87992019"
---
# <a name="troubleshoot-cache-and-memory-manager-performance-issues"></a>排查缓存和内存管理器性能问题

在 Windows Server 2012 之前，有两个主要可能的问题导致系统文件缓存的增长，直到在某些工作负载下的可用内存即将耗尽。 当这种情况导致系统缓慢时，可以确定服务器是否面对了这些问题之一。


## <a name="counters-to-monitor"></a>要监视的计数器

-   内存 \\ 长期平均备用缓存生存期 (s) &lt; 1800 秒

-   内存 \\ 可用兆字节低

-   内存 \\ 系统缓存驻留字节数

如果内存 \\ 可用的兆字节数较低，并且在同一时间内存 \\ 系统缓存驻留字节消耗的物理内存很大，则可以使用[RAMMAP](/sysinternals/downloads/rammap)来找出缓存的用途。

## <a name="system-file-cache-contains-ntfs-metafile-data-structures"></a>系统文件缓存包含 NTFS 图元文件数据结构


RAMMAP 输出中的活动图元文件页面非常多，如下图所示。 此问题可能已在繁忙的服务器上被访问，因为正在访问数百万个文件，因此将不会从缓存中释放 NTFS 图元文件数据。

![rammap 视图](../../media/perftune-guide-rammap.png)

用于通过*DynCache*工具缓解的问题。 在 Windows Server 2012 + 中，体系结构经过了重新设计，此问题不再存在。

## <a name="system-file-cache-contains-memory-mapped-files"></a>系统文件缓存包含内存映射文件


此问题在 RAMMAP 输出中有大量活动映射的文件页面。 这通常表示服务器上的某些应用程序使用[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea) API 打开大量使用文件 \_ 标志 \_ 随机访问标志的大型文件 \_ 。

知识库文章[2549369](https://support.microsoft.com/default.aspx?scid=kb;en-US;2549369)中详细描述了此问题。 "文件 \_ 标志 \_ 随机访问" \_ 标志是一个提示，用于缓存管理器在内存中保留文件的映射视图 (，直到内存管理器不) 内存不足条件。 同时，此标志指示缓存管理器禁用文件数据的预提取。

在 Windows Server 2012 + 中进行工作集修整改进后，这种情况已被缓解为某种程度，但问题本身也需要由应用程序供应商通过使用文件 \_ 标志 \_ 随机 \_ 访问来解决。 应用程序供应商的替代解决方案可能是在访问文件时使用低内存优先级。 这可以通过使用[SetThreadInformation](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadinformation) API 来实现。 更主动地从工作集中删除以低内存优先级访问的页面。

从 Windows Server 2016 开始，缓存管理器进一步减轻了这一点，因为在进行修整决策时忽略了 FILE_FLAG_RANDOM_ACCESS，因此它的处理方式与没有 FILE_FLAG_RANDOM_ACCESS 标志的任何其他文件一样， (缓存管理器仍采用此标志来禁用文件数据) 的预提取。如果有大量使用此标志打开的文件并以真正随机的方式进行访问，仍可以导致系统缓存膨胀。 强烈建议应用程序不使用 FILE_FLAG_RANDOM_ACCESS。