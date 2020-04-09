---
title: ksetup：域
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bfaa8a37ae4ee5c9669b09f27a73b3d016324dea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841580"
---
# <a name="ksetupdomain"></a>ksetup：域



设置所有 Kerberos 操作的域名。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /domain <DomainName>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<DomainName >|要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 contoso.com 或 contoso。|

## <a name="remarks"></a>备注

无。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

使用/mapuser 子命令建立与有效域（如 Microsoft）的连接：
```
ksetup /mapuser principal@realm domain-user /domain domain-name
```
当连接成功时，你将收到一个新的 TGT，或者将刷新现有 TGT。

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)