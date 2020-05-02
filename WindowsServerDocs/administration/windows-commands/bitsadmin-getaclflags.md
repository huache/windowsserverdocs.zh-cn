---
title: bitsadmin getaclflags
description: Bitsadmin getaclflags 命令的参考主题，它检索访问控制列表（ACL）传播标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 99266def-7479-4430-a61c-98ec433fa88b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a9ca541b488c3c83e7a64a138bae0914001778e3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718177"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

检索访问控制列表（ACL）传播标志，以反映子对象是否继承项。

## <a name="syntax"></a>语法

```
bitsadmin /getaclflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>备注

返回以下一个或多个标志值：

- **o** -将所有者信息复制到文件。

- **g** -复制组信息和文件。

- **d** -使用文件复制随机访问控制列表（DACL）信息。

- **s** -使用文件复制系统访问控制列表（SACL）信息。

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的访问控制列表传播标志：

```
bitsadmin /getaclflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
