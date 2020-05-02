---
title: bitsadmin geterrorcount
description: Bitsadmin geterrorcount 命令的参考主题，它检索指定作业产生暂时性错误的次数的计数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 516bd02ed296a2eba75e174c6f084926bde63e90
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718009"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount

检索指定的作业生成的暂时性错误的次数计数。

## <a name="syntax"></a>语法

```
bitsadmin /geterrorcount <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的错误计数信息：

```
bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
