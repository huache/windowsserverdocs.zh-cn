---
title: “选择设备” 列表
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 69b105a1-9710-4a06-8102-38cc9e475ca5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b36600ff4de16bf35b1c2067efac9b13957cefaa
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841030"
---
# <a name="list"></a>“选择设备” 列表



显示磁盘中的分区、磁盘中的卷或虚拟硬盘（Vhd）的列表。

## <a name="syntax"></a>语法

```
list { disk | partition | volume | vdisk }
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|disk|显示磁盘及其相关信息的列表，如磁盘的大小、可用空间、磁盘是基本磁盘还是动态磁盘，以及该磁盘使用的分区形式是主启动记录 (MBR) 还是 GUID 分区表 (GPT)。|
|partition|显示当前磁盘的分区表中列出的分区。|
|卷|显示所有磁盘上基本卷和动态卷的列表。|
|vdisk|显示附加和/或所选 Vhd 的列表。 此命令列出分离的 Vhd （如果当前已选中）;但是，在附加 VHD 之前，磁盘类型设置为 "未知"。 用星号（*）标记的 VHD 具有焦点。</br>注意：此命令仅适用于 Windows 7 和 Windows Server 2008 R2。|

## <a name="remarks"></a>备注

-   在动态磁盘上列出分区时，分区可能不与磁盘上的动态卷相对应。 出现这种不一致的原因是动态磁盘在分区表中包含用于系统卷或启动卷的项（如果磁盘上有的话）。 它们还包含占用磁盘剩余部分的分区，以便保留空间供动态卷使用。
-   用星号（*）标记的对象具有焦点。
-   列出磁盘时，如果磁盘缺失，则其磁盘号以 M 为前缀。例如，第一个缺失磁盘的编号为 M0。

## <a name="examples"></a><a name=BKMK_examples></a>示例

```
list disk
list partition
list volume
list vdisk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

