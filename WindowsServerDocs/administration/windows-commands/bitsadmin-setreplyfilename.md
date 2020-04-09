---
title: bitsadmin setreplyfilename
description: 适用于 bitsadmin setreplyfilename 的 Windows 命令主题，用于指定包含服务器回复的文件的路径。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd45174a7deac89cc943fb19d544e372c0198139
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849180"
---
# <a name="bitsadmin-setreplyfilename"></a>bitsadmin setreplyfilename

指定包含服务器答复的文件的路径。

**BITS 1.2 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /SetReplyFileName <Job> <Path>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Path|服务器答复位置|

## <a name="remarks"></a>备注

仅对上传-答复作业有效。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例设置 pathfor 名为*myDownloadJob*的作业的答复文件名。
```
C:\>bitsadmin /SetReplyFileName myDownloadJob c:\reply
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)