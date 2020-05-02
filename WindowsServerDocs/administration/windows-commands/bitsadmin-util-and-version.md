---
title: bitsadmin util 和 version
description: Bitsadmin util 和 version 命令的参考主题，其中显示了 BITS 服务的版本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20c3db6e6fcd5ef3d00287f36c9f9624ab5224dd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707595"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util 和 version

显示 BITS 服务的版本（例如，2.0）。

> [!NOTE]
> BITS 1.5 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /version [/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /verbose | 使用此开关可以显示每个与 BITS 相关的 DLL 的文件版本，并验证 BITS 服务是否可以启动。|

## <a name="examples"></a>示例

显示 BITS 服务的版本。

```
bitsadmin /util /version
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin util 命令](bitsadmin-util.md)

- [bitsadmin 命令](bitsadmin.md)
