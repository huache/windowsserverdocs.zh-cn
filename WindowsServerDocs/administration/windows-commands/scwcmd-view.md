---
title: Scwcmd 视图
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7995959a-d93e-4865-a6a0-2ab18c2bb47f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36c6422a0118b0c6d6d70adbadfb401532121c3f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835060"
---
# <a name="scwcmd-view"></a>Scwcmd: view

> 适用于：Windows Server 2012 R2、Windows Server 2012

使用指定的 .xsl 转换呈现 .xml 文件。 此命令可用于通过使用不同的视图显示安全配置向导（SCW） .xml 文件。

## <a name="syntax"></a>语法

```
scwcmd view /x:<Xmlfile.xml> [/s:<Xslfile.xsl>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/x：\<Xmlfile >|指定要查看的 .xml 文件。 必须指定此参数。|
|/s：\<Xslfile >|指定作为呈现过程的一部分应用于 .xml 文件的 .xsl 转换。 对于 SCW .xml 文件，此参数是可选的。 当使用**view**命令呈现某个 SCW .xml 文件时，它会自动尝试为指定的 .xml 文件加载正确的默认转换。 如果指定了 .xsl 转换，则必须假定 .xml 文件位于与 .xsl 转换相同的目录中，以写入转换。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

若要使用 Policyview 转换查看 Policyfile，请键入：
```
scwcmd view /x:C:\policies\Policyfile.xml /s:C:\viewers\Policyview.xsl
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)