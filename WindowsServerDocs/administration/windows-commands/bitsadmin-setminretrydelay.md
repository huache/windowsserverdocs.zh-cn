---
title: bitsadmin setminretrydelay
description: 适用于 bitsadmin setminretrydelay 的 Windows 命令主题，它设置在尝试传输文件之前，BITS 等待的最短时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce8674ca-6cc5-4bb2-8dda-7dfbb1cd6830
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fb2fe4c6d0e4f90c6ec49fa1da63404393d4f634
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849360"
---
# <a name="bitsadmin-setminretrydelay"></a>bitsadmin setminretrydelay

设置在尝试传输文件之前，在遇到暂时性错误后 BITS 等待的最小时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /SetMinRetryDelay <Job> <RetryDelay>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|RetryDelay|以秒表示的数字。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myDownloadJob*的作业的最小重试延迟设置为35秒。
```
C:\>bitsadmin /SetMinRetryDelay myDownloadJob 35
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)