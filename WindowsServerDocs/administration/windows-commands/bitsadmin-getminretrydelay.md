---
title: bitsadmin getminretrydelay
description: Windows 命令主题，适用于**bitsadmin getminretrydelay**，它检索在尝试传输文件之前服务遇到暂时性错误的时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d79ffdf1f45b0198b4af535ed83154c3c2ec24f4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850620"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

检索在尝试传输文件之前服务遇到暂时性错误后将等待的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的最小重试延迟 *myDownloadJob*。

```
C:\>bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)