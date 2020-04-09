---
title: bdehdcfg system.io.driveinfo
description: 适用于**bdehdcfg system.io.driveinfo**的 Windows 命令主题，其中显示驱动器号、总大小、最大可用空间和分区特征。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2d065e7-eced-4509-a1a0-ee2521a7f02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c598ea2d1d140090d623b3b48dbcc1be51ee66c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851060"
---
# <a name="bdehdcfg-driveinfo"></a>bdehdcfg： system.io.driveinfo

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示驱动器号、总大小、最大可用空间和分区特征。 仅列出了有效的分区。 如果已存在四个主分区或扩展分区，则不会列出未分配的空间。

有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
bdehdcfg -driveinfo <DriveLetter>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| <DriveLetter> | 指定后跟冒号的驱动器号。 |

## <a name="remarks"></a>备注

命令仅提供信息，不对驱动器进行任何修改。

## <a name="example"></a><a name=BKMK_Examples></a>实例

下面的示例将显示驱动器 C 的驱动器信息。

```
bdehdcfg  driveinfo C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
