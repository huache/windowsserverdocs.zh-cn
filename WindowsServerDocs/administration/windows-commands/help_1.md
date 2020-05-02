---
title: 帮助
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6887edfd41895bb151c5aaebb88d8b72198f4dbf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724899"
---
# <a name="help"></a>帮助

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定命令的可用命令或详细帮助信息的列表。  
  
  
  
## <a name="syntax"></a>语法  
  
```  
help [<command>]  
```  
  
### <a name="parameters"></a>参数  
  
| 参数 |                              描述                              |
|-----------|-----------------------------------------------------------------------|
| <command> | 指定要显示其详细帮助信息的命令。 |
  
## <a name="remarks"></a>备注  
  
-   如果未指定命令，则 "**帮助**" 将显示所有可能的命令。  
  
## <a name="examples"></a>示例  
若要显示 DiskPart 中可用的所有命令的列表，请键入：  
  
```  
help  
```  
  
若要显示有关如何使用 DiskPart 中的**create partition primary**命令的详细帮助信息，请键入：  
  
```  
help create partition primary  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

