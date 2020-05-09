---
title: create
description: Create 命令的参考主题，可在磁盘上创建分区或卷影分区，在一个或多个磁盘上创建卷，或在虚拟硬盘（VHD）上创建卷影分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b45acde1-8f4f-4ec3-b905-d8188f884af8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f371bee591e29a45b1488b2c36112b55ed54d3f8
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993192"
---
# <a name="create"></a>create

在磁盘上创建分区或卷影，或在一个或多个磁盘或虚拟硬盘（VHD）上创建卷影。 如果使用此命令在卷影磁盘上创建卷，则卷影副本集中必须至少包含一个卷。

## <a name="syntax"></a>语法

```
create partition
create volume
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [create partition primary 命令](create-partition-primary.md) | 在基本磁盘上创建一个具有焦点的主分区。 |
| [create partition efi 命令](create-partition-efi.md) | 在基于 Itanium 的计算机上的 GUID 分区表（gpt）磁盘上创建可扩展固件接口（EFI）系统分区。 |
| [create partition extended 命令](create-partition-extended.md) | 在具有焦点的磁盘上创建扩展分区。 |
| [create partition 逻辑命令](create-partition-logical.md) | 在现有扩展分区中创建逻辑分区。 |
| [create partition msr 命令](create-partition-msr.md) | 在 GUID 分区表（gpt）磁盘上创建 Microsoft 保留（MSR）分区。 |
| [create volume simple 命令](create-volume-simple.md) | 在指定的动态磁盘上创建简单卷。 |
| [创建卷镜像命令](create-volume-mirror.md) | 使用两个指定的动态磁盘创建卷镜像。 |
| [创建卷 raid 命令](create-volume-raid.md) | 使用三个或更多指定的动态磁盘创建一个 RAID-5 卷。 |
| [创建卷条带化命令](create-volume-stripe.md) | 使用两个或更多指定的动态磁盘创建带区卷。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
