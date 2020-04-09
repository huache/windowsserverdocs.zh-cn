---
title: logman
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb6654cce0e23ac08a2fa6334d6144b08c8b65f3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840400"
---
# <a name="logman"></a>logman

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

**logman**创建并管理事件跟踪会话和性能日志，并通过命令行支持性能监视器的许多功能。
## <a name="syntax"></a>语法
```
logman [create | query | start | stop | delete| update | import | export | /?] [options]
```
## <a name="actions"></a>Actions
|操作|说明|
|-----|--------|
|[logman create](logman-create.md)|创建计数器、跟踪、配置数据收集器或 API。|
|[logman query](logman-query.md)|查询数据收集器属性。|
|[logman start &#124; stop](logman-start-stop.md)|开始或停止数据收集。|
|[logman delete](logman-delete.md)|删除现有的数据收集器。|
|[logman update](logman-update.md)|更新现有数据收集器的属性。|
|[logman import &#124; export](logman-import-export.md)|从 XML 文件导入数据收集器集，或将数据收集器集导出到 XML 文件。|
