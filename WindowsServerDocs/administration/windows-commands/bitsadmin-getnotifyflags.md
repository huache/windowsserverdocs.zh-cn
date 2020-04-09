---
title: bitsadmin getnotifyflags
description: 适用于**bitsadmin getnotifyflags**的 Windows 命令主题，它检索指定作业的通知标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d4657e6c-8959-4db7-a4af-e73d3f80ecf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3138baea05f793cfb587d3f8fb669d446daea6b5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850580"
---
# <a name="bitsadmin-getnotifyflags"></a>bitsadmin getnotifyflags

检索指定的作业的通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifyflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

作业可以包含以下一个或多个通知标志：

| Flag | 说明 |
| ----- | ----- |
| 0x001 | 生成该作业中的所有文件都已都转移时发生的事件。 |
| 为 0x002 | 生成一个事件时发生错误。 |
| 0x004 | 禁用通知。 |
| 0x008 | 生成在修改作业或使传输进度事件。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的通知标志 *myDownloadJob*。

```
C:\>bitsadmin /getnotifyflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)