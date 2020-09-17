---
title: 仅在来宾操作系统支持时配置 SCSI 控制器
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 861f194f-467e-4b07-a1c5-55b35f6327c4
ms.date: 8/16/2016
ms.openlocfilehash: cadf4c0d0ce8cdd50d66a61f428b3e547dd457dc
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746992"
---
# <a name="configure-scsi-controllers-only-when-supported-by-the-guest-operating-system"></a>仅在来宾操作系统支持时配置 SCSI 控制器

>适用于：Windows Server 2016



|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*为虚拟机配置的 SCSI 控制器不能使用，因为来宾操作系统不支持 SCSI 控制器。*

## <a name="impact"></a>影响

*虚拟机不能使用附加到 SCSI 控制器的存储。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法

*关闭虚拟机，并使用 Hyper-v 管理器从虚拟机中删除 SCSI 控制器。然后，重新启动虚拟机。*



