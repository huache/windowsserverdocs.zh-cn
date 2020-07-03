---
title: bitsadmin setminretrydelay
description: Bitsadmin setminretrydelay 命令的参考文章，它设置在尝试传输文件之前，在遇到暂时性错误后 BITS 等待的最短时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce8674ca-6cc5-4bb2-8dda-7dfbb1cd6830
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a28bdcc90fdeee4d5173272c8670f9d0bff3c0a0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927686"
---
# <a name="bitsadmin-setminretrydelay"></a>bitsadmin setminretrydelay

设置在尝试传输文件之前，在遇到暂时性错误后 BITS 等待的最小时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /setminretrydelay <job> <retrydelay>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| retrydelay | 传输过程中出错后，BITS 等待的最小时间长度（以秒为单位）。 |

## <a name="examples"></a>示例

若要将名为*myDownloadJob*的作业的最小重试延迟设置为35秒：

```
bitsadmin /setminretrydelay myDownloadJob 35
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
