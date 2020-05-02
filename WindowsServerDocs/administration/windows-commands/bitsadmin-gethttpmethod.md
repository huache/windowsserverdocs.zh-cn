---
title: bitsadmin gethttpmethod
description: Bitsadmin gethttpmethod 命令的参考主题，用于获取用于作业的 HTTP 谓词。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: a458322a5ace69df74df054a537a7365da9e7329
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717882"
---
# <a name="bitsadmin-gethttpmethod"></a>bitsadmin gethttpmethod

获取要用于作业的 HTTP 谓词。

## <a name="syntax"></a>语法

```
bitsadmin /gethttpmethod <Job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索用于名为*myDownloadJob*的作业的 HTTP 谓词：

```
bitsadmin /gethttpmethod myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
