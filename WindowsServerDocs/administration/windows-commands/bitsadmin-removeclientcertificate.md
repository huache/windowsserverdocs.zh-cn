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
ms.openlocfilehash: 38cf00dc48ff036e7d710fb7436f00fd9381dd0b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849870"
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

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例从名为*myDownloadJob*的作业中删除客户端证书。

```
C:\>bitsadmin /removeclientcertificate myDownloadJob 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)