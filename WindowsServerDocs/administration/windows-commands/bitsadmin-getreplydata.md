---
title: bitsadmin getreplydata
description: Bitsadmin getreplydata 命令的参考文章，该命令以十六进制格式为作业检索服务器的上载答复数据。
ms.topic: reference
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a15dc59d9487ed928954f8d5cbd47828c2b58291
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631722"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

检索该作业的服务器的上传-答复数据（十六进制格式）。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getreplydata <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的上传-答复数据：

```
bitsadmin /getreplydata myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
