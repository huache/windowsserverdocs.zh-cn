---
title: bitsadmin setnotifycmdline
description: 适用于**bitsadmin setnotifycmdline**的 Windows 命令主题，用于设置在作业完成传输数据时或作业进入状态时将运行的命令行命令。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b268b68cbd355a7fe7f993d678a98f6fcb99f0ab
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122896"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

设置在作业完成传输数据或作业进入指定状态时将运行的命令行命令。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /setnotifycmdline <job> <program_name> [program_parameters]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| program_name | 作业完成时要运行的命令的名称。 可以将此值设置为 NULL，但如果这样做，则还必须将*program_parameters*设置为 null。 |
| program_parameters | 要传递给*program_name*的参数。 可以将此值设置为 NULL。 如果*program_parameters*未设置为 NULL，则*program_parameters*中的第一个参数必须与*program_name*匹配。 |

## <a name="examples"></a>示例

下面的示例在名为*myDownloadJob*的作业完成后，将服务使用的命令行命令设置为运行 notepad.exe。

```
C:\>bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe NULL
```

```
C:\>bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)