---
title: ftp lcd
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 646cbfe3feadb63388694218758dae165ffb49c4
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725266"
---
# <a name="ftp-lcd"></a>ftp： lcd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改本地计算机上的工作目录。 默认情况下，工作目录是启动**ftp**的目录。   
## <a name="syntax"></a>语法  
```  
lcd [<directory>]  
```  
#### <a name="parameters"></a>参数  
|参数|描述|  
|-------|--------|  
|[<directory>]|指定要更改的本地计算机上的目录。 如果未指定*目录*，则将当前工作目录更改为默认目录。|  
## <a name="examples"></a>示例  
将本地计算机上的工作目录更改为**C:\dir1**  
```  
lcd C:\dir1  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
