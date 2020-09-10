---
title: bitsadmin removeclientcertificate
description: Bitsadmin removeclientcertificate 命令的参考文章，用于从作业中删除客户端证书。
ms.topic: reference
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f2c739c1e1b1b3ee31d592adfb17e363dde865bf
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631159"
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

若要从名为 *myDownloadJob*的作业中删除客户端证书：

```
bitsadmin /removeclientcertificate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
