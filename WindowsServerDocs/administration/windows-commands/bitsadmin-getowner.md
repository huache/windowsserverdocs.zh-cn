---
title: bitsadmin getowner
description: Bitsadmin getowner 命令的参考主题，它检索指定作业的所有者。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a345ea47232f1f4d6340e1341747c9dad92382b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717719"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

显示指定作业的所有者的显示名称或 GUID。

## <a name="syntax"></a>语法

```
bitsadmin /getowner <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要显示名为*myDownloadJob*的作业的所有者：

```
bitsadmin /getowner myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
