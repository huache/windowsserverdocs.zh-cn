---
title: 配置具有 SCSI 控制器的虚拟机，使其能够热插拔存储
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 511e1172-aeef-463d-b5dd-2bffae411ff1
ms.date: 8/16/2016
ms.openlocfilehash: 9f0cdb47206c89c4da66786e8dfd118e6a05be81
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746972"
---
# <a name="configure-a-virtual-machine-with-a-scsi-controller-to-be-able-to-hot-plug-and-hot-unplug-storage"></a>配置具有 SCSI 控制器的虚拟机，使其能够热插拔存储

>适用于：Windows Server 2016



有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*找到了未配置 SCSI 控制器的虚拟机。*

## <a name="impact"></a>影响

*对于下列虚拟机，你将无法热插拔或热拔下存储：*

\<list of virtual machine names>

使用热插拔存储的功能，可更轻松地管理虚拟机的存储需求，而无需停机。 必须先关闭没有 SCSI 控制器的虚拟机，然后才能添加或删除存储。

## <a name="resolution"></a>解决方法

*如果不需要热插拔此虚拟机的存储，则无需执行任何操作。否则，请关闭虚拟机，并向配置中添加 SCSI 控制器。*

若要使用 SCSI 控制器来热插拔存储，来宾操作系统必须运行当前版本的 integration services。



