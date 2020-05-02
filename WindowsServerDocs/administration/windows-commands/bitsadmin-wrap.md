---
title: bitsadmin wrap
description: Bitsadmin wrap 命令的参考主题，它将超出命令窗口最右边边缘的任意行输出文本包装到下一行。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8c1c2c78fd3cc78674ef497526ba236ad058fe83
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707577"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将超出命令窗口最右边边缘的任意行输出文本包装到下一行。 必须在任何其他开关之前指定此开关。

默认情况下，除[bitsadmin 监视器](bitsadmin-monitor.md)开关以外的所有开关都将输出文本换行。

## <a name="syntax"></a>语法

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ---------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的信息并包装输出文本：

```
bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
