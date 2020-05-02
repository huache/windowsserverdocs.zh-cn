---
title: bitsadmin getnoprogresstimeout
description: Bitsadmin getnoprogresstimeout 命令的参考主题，它检索在发生暂时性错误后服务将尝试传输文件的时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3ee0377bde8a438f23ca571bc9859deef92f18fb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717814"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout

检索服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getnoprogresstimeout <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的进度超时值：

```
bitsadmin /getnoprogresstimeout myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
