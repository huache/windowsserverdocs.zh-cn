---
title: pubprn
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0bc7f7e3-84e1-4359-b477-7b1a1a0bd639
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17ca9e98ef9e3423521b03c5c21be4b3f1538b62
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722781"
---
# <a name="pubprn"></a>pubprn

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将打印机发布到 active directory 域服务。

## <a name="syntax"></a>语法
```
cscript pubprn {<ServerName> | <UNCprinterpath>} 
LDAP://CN=<Container>,DC=<Container>
```

### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|\<ServerName>|指定承载要发布的打印机的 Windows 服务器的名称。 如果未指定计算机，则使用本地计算机。|
|\<UNCprinterpath>|要发布的共享打印机的通用命名约定（UNC）路径。|
|LDAP://CN =<Container>，DC =<Container>|指定要在其中发布打印机的 active directory 域服务中的容器的路径。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   **Pubprn**命令是位于%windir%\system32\ printing_Admin_Scripts\\ <language>目录中的 Visual Basic 脚本。 若要使用此命令，请在命令提示符下键入**cscript** ，后跟 pubprn 文件的完整路径，或将目录更改为相应的文件夹。 例如：
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn
    ```
-   如果提供的信息包含空格，请使用引号将文本括起来（例如， `computer Name`）。

## <a name="examples"></a>示例
若要将\\\Server1 计算机上的所有打印机发布到 MyDomain.company.Com 域中的 MyContainer 容器，请键入：
```
cscript Ppubprn Server1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```
若要将\\\Server1 服务器上的 Laserprinter1 打印机发布到 MyDomain.company.Com 域中的 MyContainer 容器，请键入：
```
cscript Ppubprn \\Server1\Laserprinter1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```

## <a name="additional-references"></a>其他参考
- [命令行语法密钥](command-line-syntax-key.md)
[打印命令参考](print-command-reference.md)
