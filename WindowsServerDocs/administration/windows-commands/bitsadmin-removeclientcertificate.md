---
title: bitsadmin removeclientcertificate
description: 适用于**bitsadmin removeclientcertificate**的 Windows 命令主题，用于从作业中删除客户端证书。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 312226b73b91385436e15c4afbb49df161258768
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123100"
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
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

下面的示例从名为*myDownloadJob*的作业中删除客户端证书。

```
C:\>bitsadmin /removeclientcertificate myDownloadJob 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)