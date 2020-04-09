---
title: bitsadmin setnotifyflags
description: 适用于 bitsadmin setnotifyflags 的 Windows 命令主题，用于设置指定作业的事件通知标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd3001fa4ae7f51cab92556f4f2f498511cca5ae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849280"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

设置指定作业的事件通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /SetNotifyFlags <Job> <NotifyFlags>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|NotifyFlags|请参阅 "备注"|

## <a name="remarks"></a>备注

**NotifyFlags**参数可以包含以下一个或多个通知标志。

|-----|-----| | 1 |当作业中的所有文件都已传输时生成事件。 || 2 |发生错误时生成事件。 || 4 |禁用通知。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例为 "已传输" 和 "错误事件" 作业设置名为 " *myDownloadJob*" 的通知标志。
```
C:\>bitsadmin /SetNotifyFlags myDownloadJob 3
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)