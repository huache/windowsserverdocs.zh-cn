---
title: bitsadmin getdescription
description: Bitsadmin getdescription 命令的参考主题，它检索指定作业的说明。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ec5fa9875ca9f669c2a43d58532d3e5e0770d550
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718072"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription

检索指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /getdescription <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的说明：

```
bitsadmin /getdescription myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
