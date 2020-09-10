---
title: bitsadmin wrap
description: Bitsadmin wrap 命令的参考文章，可将超出命令窗口最右边边缘的任意行输出文本包装到下一行。
ms.topic: reference
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 24fa50e153d52ec74ab728a132aadd1b95c7a9da
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630379"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将超出命令窗口最右边边缘的任意行输出文本包装到下一行。 必须在任何其他开关之前指定此开关。

默认情况下，除 [bitsadmin 监视器](bitsadmin-monitor.md) 开关以外的所有开关都将输出文本换行。

## <a name="syntax"></a>语法

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob* 的作业的信息并包装输出文本：

```
bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
