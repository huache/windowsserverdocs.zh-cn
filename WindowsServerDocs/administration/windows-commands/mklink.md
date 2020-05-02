---
title: mklink
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 83a607711f0abe51810aa5abf4eb731206d810c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723975"
---
# <a name="mklink"></a>mklink
创建符号链接。



## <a name="syntax"></a>语法

```
mklink [[/d] | [/h] | [/j]] <Link> <Target>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/d|创建目录符号链接。 默认情况下， **mklink**创建文件符号链接。|
|/h|创建硬链接，而不是符号链接。|
|/j|创建目录连接。|
|\<链接>|指定正在创建的符号链接的名称。|
|\<Target>|指定新符号链接引用的路径（相对或绝对路径）。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要演示如何创建和删除名为 MyFolder 和 Myfile.txt 的符号链接，请从根目录到 \Users\User1\Documents 目录，并将文件放在目录中：
```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```
## <a name="additional-references"></a>其他参考
-   [New-Item](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
-   [del](https://docs.microsoft.com/windows-server/administration/windows-commands/del)
-   [rmdir](https://docs.microsoft.com/windows-server/administration/windows-commands/rd)
