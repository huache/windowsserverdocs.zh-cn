---
title: bitsadmin getreplydata
description: Bitsadmin getreplydata 命令的参考文章，该命令以十六进制格式为作业检索服务器的上载答复数据。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 86c8a57664d6f90980212766e8e2bd2df6d95181
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926743"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

检索该作业的服务器的上传-答复数据（十六进制格式）。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getreplydata <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的上传-答复数据：

```
bitsadmin /getreplydata myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
