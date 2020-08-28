---
title: bitsadmin listfiles
description: Bitsadmin listfiles 命令的参考文章，其中列出了指定作业中的文件。
ms.topic: reference
ms.assetid: ad0d1eaa-3bd8-45e5-8f72-4da7366f0d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b6afadf78acd187b336484db47b128afb49e27fe
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024301"
---
# <a name="bitsadmin-listfiles"></a>bitsadmin listfiles

列出指定作业中的文件。

## <a name="syntax"></a>语法

```
bitsadmin /listfiles <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的文件列表，请执行以下操作：

```
bitsadmin /listfiles myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
