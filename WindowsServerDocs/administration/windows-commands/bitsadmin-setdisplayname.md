---
title: bitsadmin setdisplayname
description: 适用于 bitsadmin setdisplayname 的 Windows 命令主题，用于设置指定作业的显示名称。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 601c5b406132e70fb7d4facb97329f7456002bb4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849540"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

设置指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /SetDisplayName <Job> <DisplayName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|DisplayName|用于指定作业的显示名称的文本。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myDownloadJob*的作业的显示名称设置为*myDownloadJob2*。
```
C:\>bitsadmin /SetDisplayName myDownloadJob Download Music Job
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)