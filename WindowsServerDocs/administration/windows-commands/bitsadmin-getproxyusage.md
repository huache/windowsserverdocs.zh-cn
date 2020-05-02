---
title: bitsadmin getproxyusage
description: Bitsadmin getproxyusage 命令的参考主题，它检索指定作业的代理使用情况设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 13a3f216b1ed3c77dbbefee37d73a657525daa36
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717649"
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
