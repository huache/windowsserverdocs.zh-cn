---
title: bitsadmin suspend
description: Bitsadmin 挂起命令的参考文章，用于挂起指定的作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42257d31dbada2badc12b44b6375702ac41a91ca
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927473"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

挂起指定的作业。 如果错误地挂起了作业，则可以使用[bitsadmin resume](bitsadmin-resume.md)开关来重新启动作业。

## <a name="syntax"></a>语法

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
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
