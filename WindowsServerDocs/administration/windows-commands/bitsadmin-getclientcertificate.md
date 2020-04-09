---
title: bitsadmin getclientcertificate
description: 适用于**bitsadmin getclientcertificate**的 Windows 命令主题，用于从作业中检索客户端证书。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7c29d5c64fd172cfdd2d5d93c5ed22d519077806
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850760"
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
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例检索名为*myDownloadJob*的作业的客户端证书。

```
C:\>bitsadmin /getclientcertificate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)