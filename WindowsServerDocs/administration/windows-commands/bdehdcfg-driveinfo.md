---
title: bdehdcfg driveinfo
description: 用于显示驱动器号、总大小、最大可用空间和分区特征的 bdehdcfg system.io.driveinfo 命令的参考文章。
ms.topic: reference
ms.assetid: f2d065e7-eced-4509-a1a0-ee2521a7f02e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: fb474e40e92979f5f2cf73d90a553bbf785c0312
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632963"
---
# <a name="bdehdcfg-driveinfo"></a>bdehdcfg： system.io.driveinfo

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示驱动器号、总大小、最大可用空间和分区特征。 仅列出了有效的分区。 如果已存在四个主分区或扩展分区，则不会列出未分配的空间。

>[!NOTE]
> 此命令仅提供信息，不会对驱动器进行任何更改。

## <a name="syntax"></a>语法

```
bdehdcfg -driveinfo <drive_letter>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| <drive_letter> | 指定后跟冒号的驱动器号。 |

## <a name="example"></a>示例

若要显示 C：驱动器的驱动器信息：

```
bdehdcfg  driveinfo C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
