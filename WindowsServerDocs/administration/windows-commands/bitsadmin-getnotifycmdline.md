---
title: bitsadmin getnotifycmdline
description: Bitsadmin getnotifycmdline 命令的参考文章，它检索在作业完成传输数据时运行的命令行命令。
ms.topic: reference
ms.assetid: 90fa33e6-aca5-4a23-82bd-19a9f13f8416
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 26b2f50520f0b77f5792b279513caedaf560eea9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631923"
---
# <a name="bitsadmin-getnotifycmdline"></a>bitsadmin getnotifycmdline

检索在指定的作业完成数据传输之后要运行的命令行命令。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifycmdline <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

在名为 *myDownloadJob* 的作业完成时检索服务使用的命令行命令。

```
bitsadmin /getnotifycmdline myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
