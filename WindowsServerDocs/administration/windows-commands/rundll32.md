---
title: rundll32
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46d9cd64-8186-4cd4-a500-44700340fe81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 391607f6e744fe88a60cb556067cf2699eee25f5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835430"
---
# <a name="rundll32"></a>rundll32



加载并运行32位动态链接库（Dll）。 没有适用于 Rundll32.exe 的可配置设置。 为使用**rundll32.exe**命令运行的特定 DLL 提供了帮助信息。

必须从提升的命令提示符运行**rundll32.exe**命令。 若要打开提升的命令提示符，请单击 "**开始**"，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。

## <a name="syntax"></a>语法

```
Rundll32 <DLLname>
```

## <a name="commands"></a>Commands

|参数|说明|
|---------|-----------|
|[Rundll32.exe printui.dll，PrintUIEntry](rundll32-printui.md)|显示打印机用户界面|

## <a name="remarks"></a>备注

Rundll32.exe 只能从显式编写的 DLL 调用函数，以由 Rundll32.exe 调用。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
