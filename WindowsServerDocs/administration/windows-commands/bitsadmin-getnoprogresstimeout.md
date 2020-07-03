---
title: bitsadmin getnoprogresstimeout
description: Bitsadmin getnoprogresstimeout 命令的参考文章，用于检索在发生暂时性错误后服务尝试传输文件的时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 95884f5e6b0dc7ae01575ddf0cc12afea6d212c3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927000"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout

检索服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getnoprogresstimeout <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
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
