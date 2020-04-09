---
title: query
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 675c5128-f3cf-4e8f-8a3f-b29ab2a8b6de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d89ae8c7c526bce396b2583abc1728456f7bcc3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836820"
---
# <a name="query"></a>query

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示有关进程、会话和远程桌面会话主机（RD 会话主机）服务器的信息。

> [!NOTE]
> 在 Windows Server 2008 R2 中，“终端服务”被重命名为“远程桌面服务”。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
query process
query session
query termserver
query user
```

### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[查询进程](query-process.md)|显示有关在 rd 会话主机服务器上运行的进程的信息。|
|[查询会话](query-session.md)|显示有关 rd 会话主机服务器上的会话的信息。|
|[查询 termserver](query-termserver.md)|显示网络上所有 rd 会话主机服务器的列表。|
|[查询用户](query-user.md)|显示有关 rd 会话主机服务器上的用户会话的信息。|

## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
