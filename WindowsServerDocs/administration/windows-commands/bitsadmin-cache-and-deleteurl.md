---
title: bitsadmin 缓存和 deleteURL
description: Bitsadmin cache 和 deleteURL 命令的参考主题，用于删除给定 URL 的所有缓存条目。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 075c48e5c8c205cbbf3fe476260ec7909edcc3e6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718450"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>bitsadmin 缓存和 deleteURL

删除给定 URL 的所有缓存条目。

## <a name="syntax"></a>语法

```
bitsadmin /deleteURL URL
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| URL | 标识远程文件的统一资源定位器。 |

## <a name="examples"></a>示例

删除的`https://www.contoso.com/en/us/default.aspx`所有缓存条目：

```
bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
