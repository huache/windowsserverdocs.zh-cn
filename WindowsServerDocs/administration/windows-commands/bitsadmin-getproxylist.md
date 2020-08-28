---
title: bitsadmin getproxylist-检索指定作业的代理列表。
description: Bitsadmin getproxylist 命令的参考文章，它检索指定作业的代理列表。
ms.topic: reference
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9038f9faaedce30bfdf6025a40e3f6369805ac2a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024411"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

检索要用于指定作业的代理服务器的逗号分隔列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的代理列表：

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
