---
title: ntfrsutl
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d7721a19-5a87-4ab6-b816-65d2da2c811f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 698237380d02fb1ceb4e738c6fb4f083dd31aef3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723468"
---
# <a name="ntfrsutl"></a>ntfrsutl

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

转储 NT 文件复制服务\(NTFRS\)的内部表、线程和内存信息。 它针对本地和远程服务器运行。 在服务控制管理器\(\)中，NTFRS 的恢复设置对于查找和保留计算机上的重要日志事件至关重要。 此工具提供了一种方便的方法来查看这些设置。   
  
## <a name="syntax"></a>语法  
  
```  
ntfrsutl[idtable|configtable|inlog|outlog][<computer>]  
ntfrsutl[memory|threads|stage][<computer>]  
ntfrsutl ds[<computer>]  
ntfrsutl [sets][<computer>]  
ntfrsutl [version][<computer>]  
ntfrsutl poll[/quickly[=[<N>]]][/slowly[=[<N>]]][/now][<computer>]  
```  
  
#### <a name="parameters"></a>参数  
  
|  参数  |                                                                                                                                                                                                                                                                                                                                        描述                                                                                                                                                                                                                                                                                                                                         |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   idtable   |                                                                                                                                                                                                                                                                                                                                          ID 表                                                                                                                                                                                                                                                                                                                                          |
| configtable |                                                                                                                                                                                                                                                                                                                                  FRS 配置表                                                                                                                                                                                                                                                                                                                                   |
|    inlog    |                                                                                                                                                                                                                                                                                                                                        入站日志                                                                                                                                                                                                                                                                                                                                         |
|   outlog    |                                                                                                                                                                                                                                                                                                                                        出站日志                                                                                                                                                                                                                                                                                                                                        |
| <computer>  |                                                                                                                                                                                                                                                                                                                                  指定计算机。                                                                                                                                                                                                                                                                                                                                   |
|   memory    |                                                                                                                                                                                                                                                                                                                                        内存使用率                                                                                                                                                                                                                                                                                                                                        |
|   线程   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|    阶段 (stage)    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|     ds      |                                                                                                                                                                                                                                                                                                                         列出了 NTFRS 服务的 DS 视图。                                                                                                                                                                                                                                                                                                                          |
|    集     |                                                                                                                                                                                                                                                                                                                             指定活动的副本集                                                                                                                                                                                                                                                                                                                              |
|   version   |                                                                                                                                                                                                                                                                                                                       指定 API 和 NTFRS 服务版本。                                                                                                                                                                                                                                                                                                                        |
|    poll     | 指定当前的轮询间隔。<p>参数：<p><ul><li>**\/快速投票**\[ **\=** \[ <N> \] \] \(  \)<p><ul><li>**快速** \-轮询，直至稳定的配置 rectrieved</li><li>快速轮询每个默认分钟。 **\= ** \-</li><li>**每\= N**分钟快速\-轮询一次*N* <N></li></ul></li><li>**\/缓慢轮询缓慢**\[ **\=** \[ <N> \] \] \(\)<p><ul><li>在检索到稳定配置之前**缓慢** \-轮询缓慢</li><li>缓慢轮询每默认分钟缓慢**\= ** \-</li><li>**每\= N**分钟快速\-轮询一次*N* <N></li></ul></li><li>** \/立即** \(轮询\)</li></ul> |
|     \/?     |                                                                                                                                                                                                                                                                                                                            在命令提示符下显示帮助。                                                                                                                                                                                                                                                                                                                            |
  
## <a name="examples"></a>示例  
若要确定文件复制的轮询间隔，请执行以下操作：  
  
```  
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1  
```  
  
若要确定当前的 NTFRS 应用程序\(接口\) API 版本：  
  
```  
C:\Program Files\SupportTools>ntfrsutl version  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   - [命令行语法项](command-line-syntax-key.md)  
  
  
  

