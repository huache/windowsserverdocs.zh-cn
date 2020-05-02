---
title: bitsadmin removeclientcertificate
description: Bitsadmin removeclientcertificate 命令的参考主题，它将客户端证书从作业中删除。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 513830f6048f78aa528fa22cb590571e718452c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717068"
---
# <a name="bitsadmin-removeclientcertificate"></a>bitsadmin removeclientcertificate

从作业中删除客户端证书。

## <a name="syntax"></a>语法

```
bitsadmin /removeclientcertificate <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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
