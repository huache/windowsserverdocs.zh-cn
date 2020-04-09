---
title: prnqctl
description: 打印测试页、暂停或恢复打印机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8df9dfa7-984c-4276-bb7d-e7675e7c399e jpjofre
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: d07d8caa0568b26f5edc16258085a59ecdafcf4e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837200"
---
# <a name="prnqctl"></a>prnqctl

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

打印测试页、暂停或恢复打印机以及清除打印机队列。  

## <a name="syntax"></a>语法  
```  
cscript Prnqctl {-z | -m | -e | -x | -?} [-s <ServerName>]   
[-p <printerName>] [-u <UserName>] [-w <Password>]  
```  
### <a name="parameters"></a>参数  

|参数|说明|  
|-------|--------|  
|-z|暂停在指定了 **-p**参数的打印机上打印。|  
|-m|在指定了 **-p**参数的打印机上恢复打印。|  
|-e|打印用 **-p**参数指定的打印机上的测试页。|  
|-x|取消用 **-p**参数指定的打印机上的所有打印作业。|  
|-s \<ServerName >|指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。|  
|-p \<printerName >|指定要管理的打印机的名称。 必需。|  
|-u \<用户名 >-w \<密码 >|指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。|  
|/?|在命令提示符下显示帮助。|  

## <a name="remarks"></a>备注  
- **Prnqctl**命令是位于%windir%\system32\ printing_Admin_Scripts\\<language> 目录中的 Visual Basic 脚本。 若要使用此命令，请在命令提示符下键入**cscript** ，后跟 prnqctl 文件的完整路径，或将目录更改为相应的文件夹。 例如：  
  ```  
  cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnqctl  
  ```  
- 如果提供的信息包含空格，请使用引号将文本括起来（例如 `"computer Name"`）。  

## <a name="examples"></a><a name="BKMK_examples"></a>示例  
若要在 \\\Server1 计算机共享的 Laserprinter1 打印机上打印测试页，请键入：  
```  
cscript Prnqctl -e -s Server1 -p Laserprinter1  
```  
若要在本地计算机上的 Laserprinter1 打印机上暂停打印，请键入：  
```  
cscript Prnqctl -z -p Laserprinter1  
```  
若要取消本地计算机上 Laserprinter1 打印机上的所有打印作业，请键入：  
```  
cscript Prnqctl -x -p Laserprinter1  
```  

## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
[打印命令参考](print-command-reference.md)  
