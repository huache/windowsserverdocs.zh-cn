---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay 命令的参考文章，用于检索在尝试传输文件之前服务等待的时间长度（以秒为单位）。
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89e925dd8db3932e273552a82a497d99fd3bdb95
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894198"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

检索在尝试传输文件之前服务遇到暂时性错误后将等待的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的最小重试延迟时间：

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
