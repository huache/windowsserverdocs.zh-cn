---
title: bitsadmin removeclientcertificate
description: Bitsadmin removeclientcertificate 命令的参考文章，用于从作业中删除客户端证书。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3659f830b9462469762fcd4c7690295073400b1e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927988"
---
# <a name="bitsadmin-removeclientcertificate"></a>bitsadmin removeclientcertificate

从作业中删除客户端证书。

## <a name="syntax"></a>语法

```
bitsadmin /removeclientcertificate <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要从名为*myDownloadJob*的作业中删除客户端证书：

```
bitsadmin /removeclientcertificate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
