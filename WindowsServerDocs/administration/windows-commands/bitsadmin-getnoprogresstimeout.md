---
title: bitsadmin getnoprogresstimeout
description: Bitsadmin getnoprogresstimeout 命令的参考文章，用于检索在发生暂时性错误后服务尝试传输文件的时间长度（以秒为单位）。
ms.topic: reference
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a7f5a84b90f124cb172ad551b196cac152a332a8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631913"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout

检索服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getnoprogresstimeout <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的进度超时值：

```
bitsadmin /getnoprogresstimeout myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
