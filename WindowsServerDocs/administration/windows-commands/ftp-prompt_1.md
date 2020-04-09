---
title: ftp prompt_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d16f70226e91e2e845480be8d83481fd76af173
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843150"
---
# <a name="ftp-prompt_1"></a>ftp： prompt_1

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在**提示**模式打开和关闭之间切换。   
## <a name="syntax"></a>语法  
```  
prompt  
```  
#### <a name="parameters"></a>参数  
无  
## <a name="remarks"></a>备注  
- 默认情况下，**提示**为 on。  
- 在多个文件传输过程中的**ftp**提示符允许您有选择地检索或存储文件。  如果**提示**处于关闭状态，则**Mget**和**mput**传输所有文件。  
  ## <a name="examples"></a><a name=BKMK_Examples></a>示例  
  打开和关闭提示模式。  
  ```  
  prompt  
  ```  
  ## <a name="additional-references"></a>其他参考  
- - [命令行语法项](command-line-syntax-key.md)  
