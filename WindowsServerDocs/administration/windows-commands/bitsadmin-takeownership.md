---
title: bitsadmin takeownership
description: 适用于 bitsadmin takeownership 的 Windows 命令主题，它允许具有管理权限的用户取得指定作业的所有权。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a2c0bfc1fcb1606102aece76129c49aad701ead
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849020"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership

允许具有管理权限的用户取得指定作业的所有权。

## <a name="syntax"></a>语法

```
bitsadmin /TakeOwnership <Job>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例获取名为*myDownloadJob*的作业的所有权。
```
C:\>bitsadmin /TakeOwnership myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)