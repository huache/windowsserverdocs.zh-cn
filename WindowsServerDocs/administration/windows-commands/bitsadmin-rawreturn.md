---
title: bitsadmin rawreturn
description: 用于返回适用于分析的数据的 bitsadmin rawreturn 命令的参考文章。
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 88b1e45d7fad2820a77d9f445065ae0ca182abb6
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893422"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

返回适合解析的数据。 通常，将此命令与 **/create**和 **/get*** 开关一起使用以仅接收值。 必须在其他交换机之前指定此开关。

> [!NOTE]
> 此命令从输出中去除换行符和格式设置。

## <a name="syntax"></a>语法

```
bitsadmin /rawreturn
```

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的状态的原始数据：

```
bitsadmin /rawreturn /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
