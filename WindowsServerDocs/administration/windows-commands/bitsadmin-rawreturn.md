---
title: bitsadmin rawreturn
description: 用于返回适用于分析的数据的 bitsadmin rawreturn 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b537b21678c100364406d4c59eaa02efd143e21
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926462"
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
