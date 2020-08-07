---
title: bitsadmin getclientcertificate
description: 用于从作业中检索客户端证书的 bitsadmin getclientcertificate 命令的参考文章。
ms.topic: article
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3deb42c0b29f238bfd0a3b0fddbea14833d38b4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894510"
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
