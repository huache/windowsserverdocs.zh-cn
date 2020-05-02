---
title: bitsadmin suspend
description: Bitsadmin 挂起命令的参考主题，用于挂起指定的作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8117cf9f4286994847e53dca8065da6821d47c5d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720453"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

挂起指定的作业。 如果错误地挂起了作业，则可以使用[bitsadmin resume](bitsadmin-resume.md)开关来重新启动作业。

## <a name="syntax"></a>语法

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ---------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="example"></a>示例

若要挂起名为*myDownloadJob*的作业：


```
bitsadmin /suspend myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin resume 命令](bitsadmin-resume.md)

- [bitsadmin 命令](bitsadmin.md)
