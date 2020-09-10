---
title: bitsadmin getproxybypasslist
description: Bitsadmin getproxybypasslist 命令的参考文章，它检索指定作业的代理跳过列表。
ms.topic: reference
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5b9b9ffd3865ef70408c566bdd832005e74f6598
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631757"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

检索指定作业的代理跳过列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxybypasslist <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>备注

旁路列表包含不是通过代理路由的主机名或 IP 地址。 此列表可以包含 `<local>` 以引用同一 LAN 上的所有服务器。 列表可以为分号 (; ) 或以空格分隔。

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的代理跳过列表：

```
bitsadmin /getproxybypasslist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
