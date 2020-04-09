---
title: bitsadmin setdescription
description: 适用于 bitsadmin setdescription 的 Windows 命令主题，用于设置指定作业的说明。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a17f864e3bc3b3cdc8ba0d76d553bcfcef27d29
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849560"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

设置指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /SetDescription <Job> <Description>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|说明|用于描述作业的文本。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业的说明。
```
C:\>bitsadmin /SetDescription myDownloadJob Music Downloads
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)