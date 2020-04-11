---
title: bitsadmin wrap
description: '**Bitsadmin wrap**的 Windows 命令主题，该主题将超出命令窗口最右边边缘的任何输出文本包装到下一行。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e754a765d94661baf24190431b455584d29991ec
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122566"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将超出命令窗口最右边边缘的任意行输出文本包装到下一行。 必须在任何其他开关之前指定此开关。

默认情况下，除[bitsadmin 监视器](bitsadmin-monitor.md)开关以外的所有开关都将输出文本换行。

## <a name="syntax"></a>语法

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

下面的示例将检索名为*myDownloadJob*的作业的信息，并对输出进行包装。

```
C:\>bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
