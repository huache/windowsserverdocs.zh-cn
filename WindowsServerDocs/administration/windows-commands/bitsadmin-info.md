---
title: bitsadmin info
description: Bitsadmin info 命令的参考文章，其中显示有关指定作业的摘要信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0b9a284ee1e0ab8501f0fb6bc3417ca399996a08
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926553"
---
# <a name="bitsadmin-info"></a>bitsadmin info

显示有关指定作业的摘要信息。

## <a name="syntax"></a>语法

```
bitsadmin /info <job> [/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| /verbose | 可选。 提供有关每个作业的详细信息。 |

## <a name="examples"></a>示例

若要检索有关名为*myDownloadJob*的作业的信息：

```
bitsadmin /info myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin info](bitsadmin-info.md)
