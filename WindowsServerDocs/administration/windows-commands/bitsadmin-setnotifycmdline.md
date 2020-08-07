---
title: bitsadmin setnotifycmdline
description: Bitsadmin setnotifycmdline 命令的参考文章，用于设置在作业完成传输数据时或作业进入状态时将运行的命令行命令。
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a81b4521d8c765d85e6b4a92d0429b128f43198e
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893008"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

设置在作业完成数据传输或作业进入指定状态之后运行的命令行命令。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /setnotifycmdline <job> <program_name> [program_parameters]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| program_name | 作业完成时要运行的命令的名称。 可以将此值设置为 NULL，但如果这样做，则还必须将*program_parameters*设置为 null。 |
| program_parameters | 要传递给*program_name*的参数。 可以将此值设置为 NULL。 如果*program_parameters*未设置为 NULL，则*program_parameters*中的第一个参数必须与*program_name*匹配。 |

## <a name="examples"></a>示例

若要在完成名为*myDownloadJob*的作业时运行 Notepad.exe：

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe NULL
```

若要在 Notepad.exe 中显示 EULA 文本，则在完成名为 myDownloadJob 的作业时：

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
