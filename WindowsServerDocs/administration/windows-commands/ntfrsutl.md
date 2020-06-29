---
title: ntfrsutl
description: Ntfrsutl 命令的参考主题，它转储 NT 文件复制服务（NTFRS）的内部表、线程和内存信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d7721a19-5a87-4ab6-b816-65d2da2c811f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f931d916888a372d66a1cc06cb7543067b9b9d3b
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85472763"
---
# <a name="ntfrsutl"></a>ntfrsutl

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从本地和远程服务器转储 NT 文件复制服务（NTFRS）的内部表、线程和内存信息。 在服务控制管理器（SCM）中，NTFRS 的恢复设置对于查找和保留计算机上的重要日志事件至关重要。 此工具提供了一种方便的方法来查看这些设置。

## <a name="syntax"></a>语法

```
ntfrsutl[idtable|configtable|inlog|outlog][<computer>]
ntfrsutl[memory|threads|stage][<computer>]
ntfrsutl ds[<computer>]
ntfrsutl [sets][<computer>]
ntfrsutl [version][<computer>]
ntfrsutl poll[/quickly[=[<n>]]][/slowly[=[<n>]]][/now][<computer>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| idtable | 指定 ID 表。 |
| configtable | 指定 FRS 配置表。 |
| inlog | 指定入站日志。 |
| outlog | 指定出站日志。 |
| `<computer>` | 指定计算机。 |
| memory | 指定内存使用情况。 |
| 线程 | 指定内存使用情况。 |
| 阶段 (stage) | 指定内存使用情况。 |
| ds | 列出了 NTFRS 服务的 DS 视图。 |
| 集 | 指定活动的副本集。 |
| 版本 | 指定 API 和 NTFRS 服务版本。 |
| poll | 指定当前的轮询间隔。<ul><li>`/quickly`-迅速轮询，直到检索稳定的配置。</li><li>`/quickly=`-每隔默认分钟数快速轮询。</li><li>`/quickly=<n>`-每*n*分钟快速轮询一次。</li><li>`/slowly`-轮询速度缓慢，直到检索稳定的配置。</li><li>`/slowly=`-每隔默认分钟数缓慢轮询。</li><li>`/slowly=<n>`-每*n*分钟轮询缓慢。</li><li>`/now`-立即轮询。</li></ul>|
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要确定文件复制的轮询间隔，请键入：

```
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1
```

若要确定当前的 NTFRS 应用程序接口（API）版本，请键入：

```
C:\Program Files\SupportTools>ntfrsutl version
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
