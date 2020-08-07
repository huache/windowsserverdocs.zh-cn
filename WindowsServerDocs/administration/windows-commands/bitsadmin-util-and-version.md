---
title: bitsadmin util 和 version
description: 用于显示 BITS 服务版本的 bitsadmin util 和 version 命令的参考文章。
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c3490fe4e3eaa217b81287d8a2ed38a6fdb98279
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880793"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util 和 version

显示 BITS 服务 (的版本，例如 2.0) 。

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
