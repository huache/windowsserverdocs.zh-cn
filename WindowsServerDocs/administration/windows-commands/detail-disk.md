---
title: detail disk
description: 详细信息磁盘命令的参考主题，其中显示了所选磁盘的属性以及该磁盘上的卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 358d6762f382dc8461c73cbd557a906eb5189c6f
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993070"
---
# <a name="detail-disk"></a>detail disk

显示所选磁盘的属性和该磁盘上的卷。 在开始之前，你必须选择一个磁盘才能使此操作成功。 使用 "[选择磁盘](select-disk.md)" 命令选择磁盘，并将焦点移动到该磁盘。 如果你选择虚拟硬盘（VHD），此命令会将磁盘的总线类型显示为 "*虚拟*"。

## <a name="syntax"></a>语法

```
detail disk
```

## <a name="examples"></a>示例

若要查看所选磁盘的属性以及磁盘中的卷的相关信息，请键入：

```
detail disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [详细信息命令](detail.md)
