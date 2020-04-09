---
title: bitsadmin getpeercachingflags
description: 适用于**bitsadmin getpeercachingflags**的 Windows 命令主题，它检索确定是否可以缓存作业的文件并将其提供给对等方的标志，以及 BITS 是否可以从对等方下载作业的内容。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cdf9683d1a65400286b4604bd9420a5ab863d4af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850550"
---
# <a name="bitsadmin-getpeercachingflags"></a>bitsadmin getpeercachingflags

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索标志，该标志确定是否可以缓存作业的文件并将其提供给对等方，以及 BITS 是否可以从对等方下载作业的内容。

## <a name="syntax"></a>语法

```
bitsadmin /getpeercachingflags <job> 
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的标志。

```
C:\>bitsadmin /getpeercachingflags myJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)