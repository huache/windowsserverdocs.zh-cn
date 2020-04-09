---
title: detail volume
description: "\"详细信息\" 卷的 Windows 命令主题，其中显示当前卷所在的磁盘。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 38f2bc75-2ed6-4e80-aa74-ab83133db1cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f0441beba769066c593e77b55b9266918e5f778
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846312"
---
# <a name="detail-volume"></a>detail volume

显示当前卷所在的磁盘。

## <a name="syntax"></a>语法

```
detail volume
```

## <a name="remarks"></a>备注

-   必须选择卷，此操作才能成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。
-   卷详细信息不适用于只读卷，如 DVD-ROM 驱动器或 CD-ROM 驱动器。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要查看当前卷所在的所有磁盘，请键入：
```
detail volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

