---
title: rundll32
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46d9cd64-8186-4cd4-a500-44700340fe81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0639206b26ea58c4ec8473c0a736fda3c435021
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722239"
---
# <a name="rundll32"></a>rundll32



加载并运行32位动态链接库（Dll）。 没有适用于 Rundll32.exe 的可配置设置。 为使用**rundll32.exe**命令运行的特定 DLL 提供了帮助信息。

必须从提升的命令提示符运行**rundll32.exe**命令。 若要打开提升的命令提示符，请单击 "**开始**"，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。

## <a name="syntax"></a>语法

```
Rundll32 <DLLname>
```

## <a name="commands"></a>命令

|参数|描述|
|---------|-----------|
|[Rundll32.exe printui.dll，PrintUIEntry](rundll32-printui.md)|显示打印机用户界面|

## <a name="remarks"></a>备注

Rundll32.exe 只能从显式编写的 DLL 调用函数，以由 Rundll32.exe 调用。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
