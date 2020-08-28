---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay 命令的参考文章，用于检索在尝试传输文件之前服务等待的时间长度（以秒为单位）。
ms.topic: reference
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f5bc6d69e7dbc46bc7e0df3a34ac97f37fda252
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030305"
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
