---
title: bitsadmin util 和 enableanalyticchannel
description: Windows 命令主题，适用于 bitsadmin util 和 enableanalyticchannel，这将启用或禁用 BITS 客户端分析通道。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7302c9368649d47cd65110f4a515b527d3df2aac
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848980"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>bitsadmin util 和 enableanalyticchannel

启用或禁用 BITS 客户端分析通道。

## <a name="syntax"></a>语法

```
bitsadmin /Util /EnableAnalyticChannel TRUE|FALSE
```

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例启用 BITS 客户端分析通道。
```
C:\>bitsadmin /Util / EnableAnalyticChannel TRUE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)