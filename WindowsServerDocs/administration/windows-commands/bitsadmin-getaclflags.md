---
title: bitsadmin getaclflags
description: Bitsadmin getaclflags 命令的参考文章，它检索访问控制列表 (ACL) 传播标志。
ms.topic: reference
ms.assetid: 99266def-7479-4430-a61c-98ec433fa88b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4c5c7101db157b7fa5b56833b8d5f89619bd8d51
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632322"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

检索访问控制列表 (ACL) 传播标志，以反映子对象是否继承项。

## <a name="syntax"></a>语法

```
bitsadmin /getaclflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>备注

返回以下一个或多个标志值：

- **o** -将所有者信息复制到文件。

- **g** -复制组信息和文件。

- **d** -复制任意访问控制列表 (DACL) 包含文件的信息。

- **s** -复制系统访问控制列表 (SACL) 包含文件的信息。

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的访问控制列表传播标志：

```
bitsadmin /getaclflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
