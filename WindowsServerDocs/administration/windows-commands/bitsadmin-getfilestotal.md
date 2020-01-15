---
title: bitsadmin getfilestotal
description: 适用于**bitsadmin getfilestotal**的 Windows 命令主题-检索指定作业中的文件数。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5c28d8e970bd7db896073bf8cddb168ffe9deff
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946848"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal



检索指定的作业中的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /GetFilesTotal <Job>
```

## <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|作业|该作业的显示名称或 GUID|

## <a name="BKMK_examples"></a>示例

下面的示例检索名为作业中包含的文件数 *myDownloadJob*。
```
C:\>bitsadmin /GetFilesTotal myDownloadJob
```

## <a name="see-also"></a>另请参阅

[命令行语法项](command-line-syntax-key.md)
