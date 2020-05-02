---
title: logman query
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1116a0f0-5415-4369-a045-12f79f8f66de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 05448a4f129a59145813dd0da7199d4adf845c5c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724358"
---
# <a name="logman-query"></a>logman query

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

查询数据收集器或数据收集器集属性。  

## <a name="syntax"></a>语法  
```  
logman query [providers|Data Collector Set name] [options]  
```  
### <a name="parameters"></a>参数  

|     参数      |                                 描述                                  |
|--------------------|------------------------------------------------------------------------------|
|         /?         |                       显示区分上下文的帮助。                       |
| -s<computer name> |            在指定的远程计算机上执行命令。             |
|  -config <value>   |           指定包含命令选项的设置文件。            |
|    [-n]<name>     |                          目标对象的名称。                          |
|        -ets        | 直接将命令发送到事件跟踪会话，无需保存或计划。 |

## <a name="examples"></a>示例  
以下命令列出了在目标系统上配置的所有数据收集器集。  
```  
logman query  
```  
以下命令将列出名为 perf_log 的数据收集器集中包含的数据收集器。  
```  
logman query perf_log  
```  
以下命令将列出目标系统上所有可用的数据收集器。  
```  
logman query providers  
```  
## <a name="additional-references"></a>其他参考  
[logman](logman.md)  
