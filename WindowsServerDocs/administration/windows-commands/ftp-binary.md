---
title: ftp 二进制文件
description: Ftp 二进制文件的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20b2f72517826576cfee643eda0c54063b162c94
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843720"
---
# <a name="ftp-binary"></a>ftp：二进制

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将文件传输类型设置为 binary。   
## <a name="syntax"></a>语法  
```  
binary  
```  
#### <a name="parameters"></a>参数  
无  
## <a name="remarks-optional-section"></a>备注 <optional section>  
**ftp**支持 ASCII 和二进制图像文件传输类型。 传输可执行文件时，请使用二进制。 在二进制模式下，文件以单字节单位传输。 有关 ASCII 文件传输的详细信息，请参阅其他引用中的**ftp： ASCII** 。  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
将 "文件传输类型" 设置为 "二进制"。  
```  
binary  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
