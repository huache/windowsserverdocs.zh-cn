---
title: help
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 404cefe879e8f63678f2cba90516fad9c216eb23
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842310"
---
# <a name="help"></a>help

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示有关指定命令的可用命令或详细帮助信息的列表。  
  
  
  
## <a name="syntax"></a>语法  
  
```  
help [<command>]  
```  
  
### <a name="parameters"></a>参数  
  
| 参数 |                              说明                              |
|-----------|-----------------------------------------------------------------------|
| <command> | 指定要显示其详细帮助信息的命令。 |
  
## <a name="remarks"></a>备注  
  
-   如果未指定命令，则 "**帮助**" 将显示所有可能的命令。  
  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
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
  

  

