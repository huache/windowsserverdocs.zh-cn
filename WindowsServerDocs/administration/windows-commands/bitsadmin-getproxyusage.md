---
title: bitsadmin getproxyusage
description: Bitsadmin getproxyusage 命令的参考文章，它检索指定作业的代理使用情况设置。
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ff2320ba66cdc11781ac56900e5a4aaa9fb1dc0f
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893932"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage

检索指定作业的代理使用情况设置。

## <a name="syntax"></a>语法

```
bitsadmin /getproxyusage <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>Output

返回的代理使用值可以是：

- **预配置**-使用所有者的 Internet Explorer 默认值。

- **No_Proxy** -不使用代理服务器。

- **替代**-使用显式代理列表。

- 自动**检测-自动**检测代理设置。

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的代理用法：

```
bitsadmin /getproxyusage myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
