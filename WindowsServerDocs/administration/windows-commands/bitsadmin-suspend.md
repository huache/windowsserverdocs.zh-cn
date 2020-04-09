---
title: bitsadmin suspend
description: 用于暂停指定作业的 bitsadmin 挂起的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0419f4cdf59d04539b8b4c6d47cec886197d412b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849050"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

挂起指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /Suspend <Job>
```

### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|作业|该作业的显示名称或 GUID|

## <a name="remarks"></a>备注

若要重新启动作业，请使用[bitsadmin resume](bitsadmin-resume.md)开关。

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例挂起名为*myDownloadJob*的作业。

```
C:\>bitsadmin /Suspend myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
