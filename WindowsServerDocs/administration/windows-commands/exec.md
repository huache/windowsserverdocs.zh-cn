---
title: exec
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d39fbf948050dd00f329e461c34c2365030cb05d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844990"
---
# <a name="exec"></a>exec



在本地计算机上执行文件。 该文件可以是**cmd**脚本。

## <a name="syntax"></a>语法

```
exec <ScriptFile.cmd>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ScriptFile >|指定要执行的脚本文件。|

## <a name="remarks"></a>备注

-   此命令用于在备份或还原顺序中复制或还原数据。
-   如果脚本失败，将返回错误，并且 DiskShadow 将退出。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)