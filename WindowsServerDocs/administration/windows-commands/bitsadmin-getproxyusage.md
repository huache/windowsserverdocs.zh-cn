---
title: bitsadmin getproxyusage
description: Bitsadmin getproxyusage 命令的参考文章，它检索指定作业的代理使用情况设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad1ffe5786202d6fecc0d65a719c9d6be0f5609e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926788"
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
