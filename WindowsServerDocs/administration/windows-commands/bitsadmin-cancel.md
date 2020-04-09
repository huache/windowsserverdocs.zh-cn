---
title: bitsadmin cancel
description: 用于**bitsadmin cancel**的 Windows 命令主题，它会从传输队列中删除作业并删除与该作业关联的所有临时文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5c2bdeef824bc269671cc5ae926fb77cd5726c58
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850830"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

从传输队列中删除该作业并删除与作业关联的所有临时文件。

## <a name="syntax"></a>语法

```
bitsadmin /cancel <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例移除 *myDownloadJob* 从传输队列的作业。

```
C:\>bitsadmin /cancel myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)