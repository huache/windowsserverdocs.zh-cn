---
title: bitsadmin setpriority
description: 适用于 bitsadmin setpriority 的 Windows 命令主题，用于设置指定作业的优先级。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d007c62402a3d70910e1c79fab5c406295a63a5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849210"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

设置指定作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /SetPriority <Job> <Priority>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Priority|以下值之一：</br>-前景</br>-高</br>-正常</br>-低|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myDownloadJob*的作业的优先级设置为 normal。
```
C:\>bitsadmin /SetPriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)