---
title: bitsadmin 对等缓存和 getconfigurationflags
description: '**Bitsadmin**对等互连和**Getconfigurationflags**的 Windows 命令主题，可获取确定计算机是否向对等机提供内容以及是否可以从对等方下载内容的配置标志。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: be8d6a719d63c8e9c6250320560b6ce21274c680
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850170"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>bitsadmin 对等缓存和 getconfigurationflags

获取用于确定计算机是否向对等方提供内容以及是否可以从对等方下载内容的配置标志。

## <a name="syntax"></a>语法

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例获取名为*myDownloadJob*的作业的配置标志。

```
C:\> bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)