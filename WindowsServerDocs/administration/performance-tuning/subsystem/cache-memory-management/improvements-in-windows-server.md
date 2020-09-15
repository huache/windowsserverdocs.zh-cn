---
title: 缓存和内存管理器改进
description: Windows Server 2016 中的缓存和内存管理器改进
ms.topic: article
ms.author: pavel
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 799598223812f5992db0354780424f7da13033ea
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078004"
---
# <a name="cache-and-memory-manager-improvements"></a>缓存和内存管理器改进

本主题介绍 Windows Server 2012 和2016中的缓存管理器和内存管理器改进。

## <a name="cache-manager-improvements-in-windows-server-2016"></a>Windows Server 2016 中的缓存管理器改进
缓存管理器还添加了对真正异步缓存读取的支持。
如果应用程序严重依赖于异步缓存读取，则这可能会提高应用程序的性能。尽管大多数内置文件系统都支持异步缓存读取一段时间，但通常会由于与处理线程池和文件系统的内部工作队列相关的各种设计选择而导致性能的限制。由于支持内核正确，因此缓存管理器现在可以隐藏文件系统中的所有线程池和工作队列管理复杂性，使其更高效地处理异步缓存读取。对于每个 (系统，缓存管理器有一组控件 datastructures，支持最大) VHD 嵌套级别以最大程度地提高并行度。


## <a name="cache-manager-improvements-in-windows-server-2012"></a>Windows Server 2012 中的缓存管理器改进
除了缓存管理器增强功能以读取顺序工作负载的提前逻辑外，还添加了一个新的 API [CcSetReadAheadGranularityEx](/windows-hardware/drivers/ifs/ccsetreadaheadgranularityex) ，以使文件系统驱动程序（如 SMB）更改其预读参数。 它通过发送多个小型读取请求，而不是发送单个较大的提前请求，为远程文件方案提供更好的吞吐量。 只有内核组件（如文件系统驱动程序）才能以编程方式在每个文件上配置这些值。

## <a name="memory-manager-improvements-in-windows-server-2012"></a>Windows Server 2012 中的内存管理器改进
启用页面组合可能会减少服务器上的内存使用率，这些页面具有的内容完全相同。 例如，运行同一内存密集型应用程序的多个实例的服务器或使用高重复数据的单个应用程序，可能是尝试进行页面组合的最佳候选项。 启用页面合并的缺点是增加了 CPU 使用率。

下面是一些服务器角色的示例，其中的页面合并不太可能提供很多好处：

-   文件服务器 (大部分内存由不是私有的，因此不可组合的文件页面使用) 

-   配置为使用 AWE 或大型页面 (大多数内存的 Microsoft SQL Server 是专用的但不可分页的) 

默认情况下，页面组合处于禁用状态，但可以使用 [Mmagent.ps1](/powershell/module/mmagent/enable-mmagent?view=win10-ps) Windows PowerShell cmdlet 启用。 Windows Server 2012 中添加了页面组合。