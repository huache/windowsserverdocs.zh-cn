---
title: ntfrsutl
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d7721a19-5a87-4ab6-b816-65d2da2c811f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 14e718550247b8854073407146456d366d562d2b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837990"
---
# <a name="ntfrsutl"></a>ntfrsutl

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

转储 NT 文件复制服务 \(NTFRS\)的内部表、线程和内存信息。 它针对本地和远程服务器运行。 在服务控制管理器中，NTFRS 的恢复设置 \(SCM\) 对于在计算机上查找和保存重要日志事件至关重要。 此工具提供了一种方便的方法来查看这些设置。   
  
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
  
|  参数  |                                                                                                                                                                                                                                                                                                                                        说明                                                                                                                                                                                                                                                                                                                                         |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   idtable   |                                                                                                                                                                                                                                                                                                                                          ID 表                                                                                                                                                                                                                                                                                                                                          |
| configtable |                                                                                                                                                                                                                                                                                                                                  FRS 配置表                                                                                                                                                                                                                                                                                                                                   |
|    inlog    |                                                                                                                                                                                                                                                                                                                                        入站日志                                                                                                                                                                                                                                                                                                                                         |
|   outlog    |                                                                                                                                                                                                                                                                                                                                        出站日志                                                                                                                                                                                                                                                                                                                                        |
| <computer>  |                                                                                                                                                                                                                                                                                                                                  指定计算机。                                                                                                                                                                                                                                                                                                                                   |
|   内存    |                                                                                                                                                                                                                                                                                                                                        内存使用率                                                                                                                                                                                                                                                                                                                                        |
|   线程   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|    区域    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|     Ds      |                                                                                                                                                                                                                                                                                                                         列出了 NTFRS 服务的 DS 视图。                                                                                                                                                                                                                                                                                                                          |
|    集     |                                                                                                                                                                                                                                                                                                                             指定活动的副本集                                                                                                                                                                                                                                                                                                                              |
|   version   |                                                                                                                                                                                                                                                                                                                       指定 API 和 NTFRS 服务版本。                                                                                                                                                                                                                                                                                                                        |
|    poll     | 指定当前的轮询间隔。<p>参数：<p><ul><li>**\/快速**\[ **\=** \[ <N>\]\]\(  \)<p><ul><li>**快速 \- 轮询**，直至稳定的配置 rectrieved</li><li>每隔默认分钟快速 **\=** \- 轮询。</li><li>每*N*分钟快速 **\=** <N> \- 轮询</li></ul></li><li>**\/慢慢**\[ **\=** \[ <N>\]\] 轮询缓慢 \(\)<p><ul><li>**缓慢 \- 轮询**，直到检索到稳定的配置</li><li>**缓慢\=** \- 每隔默认分钟缓慢轮询</li><li>**缓慢\=** <N> \- 每*N*分钟迅速轮询</li></ul></li><li>**现在\/** \(轮询\)</li></ul> |
|     \/？     |                                                                                                                                                                                                                                                                                                                            在命令提示符下显示帮助。                                                                                                                                                                                                                                                                                                                            |
  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
若要确定文件复制的轮询间隔，请执行以下操作：  
  
```  
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1  
```  
  
若要确定当前的 NTFRS 应用程序接口 \(API\) 版本：  
  
```  
C:\Program Files\SupportTools>ntfrsutl version  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   - [命令行语法项](command-line-syntax-key.md)  
  
  
  

