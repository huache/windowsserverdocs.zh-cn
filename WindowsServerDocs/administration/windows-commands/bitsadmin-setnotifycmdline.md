---
title: bitsadmin setnotifycmdline
description: 适用于 bitsadmin setnotifycmdline 的 Windows 命令主题，用于设置在作业完成传输数据或作业进入状态时将运行的命令行命令。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 761a7003e44e8dc15cb2dd2f1ce5a1a23be53286
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849330"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

设置在作业完成传输数据或作业进入状态时将运行的命令行命令。

**BITS 1.2 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /SetNotifyCmdLine <Job> <ProgramName> [ProgramParameters]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|ProgramName|作业完成时要运行的命令的名称。|
|ProgramParameters|要传递给*ProgramName*的参数。|

## <a name="remarks"></a>备注

可以为*ProgramName*和*ProgramParameters*指定 NULL。 如果*ProgramName*为 null，则*PROGRAMPARAMETERS*必须为 null。

> [!IMPORTANT]
> 如果*ProgramParameters*不为 NULL，则*ProgramParameters*中的第一个参数必须与*ProgramName*匹配。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例在名为*myDownloadJob*的作业完成时，将服务使用的命令行命令设置为运行记事本。
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe NULL
```
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)