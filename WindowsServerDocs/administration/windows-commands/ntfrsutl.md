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
ms.openlocfilehash: dc1275b7936a88b14b7658e2fe27d3958a035a04
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820918"
---
# <a name="ntfrsutl"></a>ntfrsutl

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

转储 NT 文件复制服务 NTFRS 的内部表、线程和内存信息 \( \) 。 它针对本地和远程服务器运行。 在服务控制管理器中，NTFRS 的恢复设置对于 \( \) 查找和保留计算机上的重要日志事件至关重要。 此工具提供了一种方便的方法来查看这些设置。

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
|   memory    |                                                                                                                                                                                                                                                                                                                                        内存使用率                                                                                                                                                                                                                                                                                                                                        |
|   线程   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|    阶段 (stage)    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|     ds      |                                                                                                                                                                                                                                                                                                                         列出了 NTFRS 服务的 DS 视图。                                                                                                                                                                                                                                                                                                                          |
|    集     |                                                                                                                                                                                                                                                                                                                             指定活动的副本集                                                                                                                                                                                                                                                                                                                              |
|   版本   |                                                                                                                                                                                                                                                                                                                       指定 API 和 NTFRS 服务版本。                                                                                                                                                                                                                                                                                                                        |
|    poll     | 指定当前的轮询间隔。<p>参数：<p><ul><li>** \/ 快速** \[ **\=** \[<N>\]\]\(快速轮询  \)<p><ul><li>**快速** \-在 rectrieved 稳定配置之前快速轮询</li><li>**快速 \= **\-每隔默认时间快速轮询。</li><li>**快速 \= ** <N>\-每*N*分钟快速轮询一次</li></ul></li><li>** \/ 缓慢** \[ **\=** \[<N>\]\]\(轮询缓慢\)<p><ul><li>**缓慢** \-轮询缓慢直到检索到稳定配置</li><li>**缓慢 \= **\-每隔一个默认分钟轮询缓慢</li><li>**缓慢 \= ** <N>\-每*N*分钟快速轮询一次</li></ul></li><li>** \/ 现在** \(立即轮询\)</li></ul> |
|     \/?     |                                                                                                                                                                                                                                                                                                                            在命令提示符下显示帮助。                                                                                                                                                                                                                                                                                                                            |

## <a name="examples"></a>示例
若要确定文件复制的轮询间隔，请执行以下操作：

```
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1
```

若要确定当前的 NTFRS 应用程序接口 \( API \) 版本：

```
C:\Program Files\SupportTools>ntfrsutl version
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)




