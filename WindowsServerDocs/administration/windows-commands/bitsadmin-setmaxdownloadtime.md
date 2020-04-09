---
title: bitsadmin setmaxdownloadtime
description: 适用于 bitsadmin setmaxdownloadtime 的 Windows 命令主题，用于设置下载超时（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd44011cd14d575a9c3798ede45641fac4c3dc75
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849370"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>bitsadmin setmaxdownloadtime

设置下载超时（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /SetMaxDownloadTime <Job> <Timeout>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|超时|超时（秒）|

## <a name="remarks"></a>备注

-   不可用

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myDownloadJob*的作业的超时值设置为10秒。
```
C:\>bitsadmin /SetMaxDownloadTime myDownloadJob 10
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)