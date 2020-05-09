---
title: detail volume
description: 详细信息卷的参考主题，其中显示了当前卷所在的磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 38f2bc75-2ed6-4e80-aa74-ab83133db1cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eac3749304a06ea4cc11bf90a3220f5e24f9b5ae
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993011"
---
# <a name="detail-volume"></a>detail volume

显示当前卷所在的磁盘。 在开始之前，你必须选择一个卷才能使此操作成功。 使用 "[选择音量](select-volume.md)" 命令选择卷并将焦点移动到该卷。 卷详细信息不适用于只读卷，如 DVD-ROM 或 CD-ROM 驱动器。

## <a name="syntax"></a>语法

```
detail volume
```

## <a name="examples"></a>示例

若要查看当前卷所在的所有磁盘，请键入：

```
detail volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [select volume](select-volume.md)

- [详细信息命令](detail.md)