---
title: rundll32
description: '适用于 * * * * 的 Windows 命令主题 '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46d9cd64-8186-4cd4-a500-44700340fe81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7345c1ad59a4209e607245db1b2a79055ffcb5fe
ms.sourcegitcommit: 1c75e4b3f5895f9fa33efffd06822dca301d4835
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77517283"
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

#### <a name="additional-references"></a>其他参考

[命令行语法项](command-line-syntax-key.md)
