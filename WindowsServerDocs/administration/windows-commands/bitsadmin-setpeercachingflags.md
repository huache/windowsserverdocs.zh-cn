---
title: bitsadmin setpeercachingflags
description: 适用于 bitsadmin setpeercachingflags 的 Windows 命令主题，用于设置标志，这些标志确定是否可以缓存作业的文件并将其提供给对等方以及作业是否可以从对等方下载内容。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d19e4d14b47e4aa96e9ad9d4367e872350ad4d43
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849240"
---
# <a name="bitsadmin-setpeercachingflags"></a>bitsadmin setpeercachingflags

设置标志，该标志确定是否可以缓存作业的文件并将其提供给对等方以及作业是否可以从对等方下载内容。

## <a name="syntax"></a>语法

```
bitsadmin /SetPeerCachingFlags <Job> <value> 
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|值|该值是一个无符号整数，它对二进制表示形式中的位进行了以下解释。</br>1-作业可以从对等方下载内容。</br>2-作业的文件可以缓存并提供给对等方。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例设置名为*myJob*的作业的标志，它允许其从对等方下载内容。
```
C:\>bitsadmin / SetPeerCachingFlags myJob 1 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)