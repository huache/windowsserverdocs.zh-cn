---
title: bitsadmin getclientcertificate
description: Bitsadmin getclientcertificate 命令的参考主题，该主题从作业中检索客户端证书。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d2582950dd02ca1880e4765fb974c83c423b22bb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718127"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate

从作业中检索客户端证书。

## <a name="syntax"></a>语法

```
bitsadmin /getclientcertificate <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的客户端证书：

```
bitsadmin /getclientcertificate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
