---
title: bitsadmin replaceremoteprefix
description: Bitsadmin replaceremoteprefix 命令的参考文章，可根据需要将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 86149b09c65f430bf0a3bbe7a1595bb5385c6dcc
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893363"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

必要时，将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。

## <a name="syntax"></a>语法

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| oldprefix | 现有的 URL 前缀。 |
| newprefix | 新的 URL 前缀。 |

## <a name="examples"></a>示例

若要将名为*myDownloadJob*的作业中的所有文件的远程 URL 更改为，则为 *http://stageserver* *http://prodserver* 。

```
bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>其他信息

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
