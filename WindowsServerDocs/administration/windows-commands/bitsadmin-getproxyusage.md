---
title: bitsadmin getproxyusage
description: Bitsadmin getproxyusage 命令的参考文章，它检索指定作业的代理使用情况设置。
ms.topic: reference
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 423168d72a88ecad90fd8de43eab3cb4486a750b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024401"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage

检索指定作业的代理使用情况设置。

## <a name="syntax"></a>语法

```
bitsadmin /getproxyusage <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

返回的代理使用值可以是：

- **预配置** -使用所有者的 Internet Explorer 默认值。

- **No_Proxy** -不使用代理服务器。

- **替代** -使用显式代理列表。

- 自动**检测-自动**检测代理设置。

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的代理用法：

```
bitsadmin /getproxyusage myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
