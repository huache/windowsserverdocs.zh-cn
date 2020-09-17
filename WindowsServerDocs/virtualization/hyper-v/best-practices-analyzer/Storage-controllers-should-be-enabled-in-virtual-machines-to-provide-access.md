---
title: 应在虚拟机中启用存储控制器以提供对附加存储的访问权限
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 532548a1-8ffe-4b5b-902e-ed2f0819012b
ms.date: 8/16/2016
ms.openlocfilehash: 5eb1767fd51253ed26c0a169be1043b633dbcbcd
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746192"
---
# <a name="storage-controllers-should-be-enabled-in-virtual-machines-to-provide-access-to-attached-storage"></a>应在虚拟机中启用存储控制器以提供对附加存储的访问权限

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*一个或多个存储控制器可能在虚拟机中被禁用。*

## <a name="impact"></a>影响

*虚拟机不能使用连接到已禁用存储控制器的存储。这会影响以下虚拟机：*

\<list of virtual machine names>

## <a name="resolution"></a>解决方法

*使用来宾操作系统中的设备管理器来启用所有存储控制器。如果不需要存储控制器，请使用 Hyper-v 管理器将其从虚拟机中删除。*

有关如何使用设备管理器的说明，请参阅来宾操作系统中的帮助。 有关如何删除存储控制器的说明，请参阅以下过程。

#### <a name="to-remove-a-scsi-storage-controller-from-the-virtual-machine"></a>从虚拟机中删除 SCSI 存储控制器

1.  打开 Hyper-V 管理器。 单击 **“开始”**，指向 **“管理工具”**，然后单击 **“Hyper-V 管理器”**。

2.  在结果窗格中的 " **虚拟机**" 下，选择要配置的虚拟机。

3.  如果虚拟机正在运行，请关闭虚拟机。 右键单击该虚拟机，然后单击 " **关闭**"。

4.  在 **“操作”** 窗格中的虚拟机名称下，单击 **“设置”**。

5.  在 " **设置** " 对话框的左窗格中的 " **硬件**" 下，单击 " **SCSI 控制器**"。

6.  在右侧窗格中，单击 " **删除**"。



