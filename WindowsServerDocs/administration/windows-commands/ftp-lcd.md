---
title: ftp lcd
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d7e2e6fc9f6af7655381bfb802dc190e79365bd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843400"
---
# <a name="ftp-lcd"></a>ftp： lcd

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改本地计算机上的工作目录。 默认情况下，工作目录是启动**ftp**的目录。   
## <a name="syntax"></a>语法  
```  
lcd [<directory>]  
```  
#### <a name="parameters"></a>参数  
|参数|说明|  
|-------|--------|  
|[<directory>]|指定要更改的本地计算机上的目录。 如果未指定*目录*，则将当前工作目录更改为默认目录。|  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
将本地计算机上的工作目录更改为**C:\dir1**  
```  
lcd C:\dir1  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
