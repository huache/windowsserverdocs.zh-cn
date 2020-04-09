---
title: delete volume
description: 删除卷的 Windows 命令主题，用于删除选定的卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2e958785c278306563999b09c1fecc0fdfa7ecb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846550"
---
# <a name="delete-volume"></a>delete volume

删除选定的卷。

## <a name="syntax"></a>语法

```
delete volume [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>备注

-   无法删除系统卷、启动卷或任何包含活动页面文件或故障转储（内存转储）的卷。
-   必须选择卷，此操作才能成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要删除具有焦点的卷，请键入：
```
delete volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

