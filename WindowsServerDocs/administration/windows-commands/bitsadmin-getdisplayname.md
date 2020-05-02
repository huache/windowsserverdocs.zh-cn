---
title: bitsadmin getdisplayname
description: Bitsadmin getdisplayname 命令的参考主题，它检索指定作业的显示名称。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f7c92fdb7c743c1a4c71f076764f5d1da2d95a6f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718031"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname

检索指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /getdisplayname <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的显示名称，请执行以下操作：

```
bitsadmin /getdisplayname myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
