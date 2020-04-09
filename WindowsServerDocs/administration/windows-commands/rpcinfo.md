---
title: rpcinfo
description: 了解如何列出远程计算机上的程序。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c342232-a8f0-42ff-8f11-d18c4981f5ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 03450a370c84eb4659b9ebfde0729fee52e6c1f6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835550"
---
# <a name="rpcinfo"></a>rpcinfo

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

列出远程计算机上的程序。 **Rpcinfo**命令行实用工具向 RPC 服务器发出远程过程调用（RPC），并报告它找到的内容。 

## <a name="syntax"></a>语法
```
rpcinfo [/p [<Node>]] [/b <Program version>] [/t <Node Program> [<version>]] [/u <Node Program> [<version>]]
```

#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/p [\<节点 >]|列出注册到指定主机上的端口映射器的所有程序。 如果未指定节点（计算机）名称，程序将查询本地主机上的端口映射器。|
|/b \<程序版本 >|请求所有网络节点的响应，这些网络节点具有注册到端口映射器的指定程序和版本。 必须同时指定程序名称或编号和版本号。|
|/t \<Node Program > [\<版本 >]|使用 TCP 传输协议调用指定的程序。 必须同时指定节点（计算机）名称和程序名称。 如果未指定版本，程序将调用所有版本。|
|/u \<Node Program > [\<版本 >]|使用 UDP 传输协议调用指定的程序。 必须同时指定节点（计算机）名称和程序名称。 如果未指定版本，程序将调用所有版本。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a><a name="BKMK_Examples"></a>示例
若要列出注册到端口映射器的所有程序，请键入：
```
rpcinfo /p [<Node>]
```
若要从具有指定程序的网络节点请求响应，请键入：
```
rpcinfo /b <Program version>
```
若要使用传输控制协议（TCP）调用程序，请键入：
```
rpcinfo /t <Node Program> [<version>]
```
使用用户数据报协议（UDP）调用程序：
```
rpcinfo /u <Node Program> [<version>]
```

## <a name="additional-references"></a>其他参考
-   - [命令行语法项](command-line-syntax-key.md)
