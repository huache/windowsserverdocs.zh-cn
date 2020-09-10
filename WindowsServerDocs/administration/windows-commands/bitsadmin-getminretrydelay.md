---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay 命令的参考文章，用于检索在尝试传输文件之前服务等待的时间长度（以秒为单位）。
ms.topic: reference
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: be71dc355e966b4a6ac627045f1ec5ceaf68f2d3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631939"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

检索在尝试传输文件之前服务遇到暂时性错误后将等待的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的最小重试延迟时间：

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
