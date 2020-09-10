---
title: bitsadmin getclientcertificate
description: 用于从作业中检索客户端证书的 bitsadmin getclientcertificate 命令的参考文章。
ms.topic: reference
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 71f1ed8920ba2bd3aa0a0f48683d8841e08afb6d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632265"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate

从作业中检索客户端证书。

## <a name="syntax"></a>语法

```
bitsadmin /getclientcertificate <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的客户端证书：

```
bitsadmin /getclientcertificate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
