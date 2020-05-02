---
title: bitsadmin getproxylist-检索指定作业的代理列表。
description: Bitsadmin getproxylist 命令的参考主题，它检索指定作业的代理列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a92703d83cc872204d3dc488c15d703dfd50a780
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717659"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

检索要用于指定作业的代理服务器的逗号分隔列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的代理列表：

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
