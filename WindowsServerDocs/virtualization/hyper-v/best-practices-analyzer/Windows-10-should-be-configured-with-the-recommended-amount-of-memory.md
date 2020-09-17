---
title: 应使用建议的内存量配置 Windows 10
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 0c810b82-b06a-4382-b598-5c642e8534be
ms.date: 8/16/2016
ms.openlocfilehash: 80bfdff229cbb70f54464a304b4d803bcba75368
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747142"
---
# <a name="windows-10-should-be-configured-with-the-recommended-amount-of-memory"></a>应使用建议的内存量配置 Windows 10

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

以下各节提供了有关特定问题的详细信息。 斜体指示在最佳做法分析器工具中显示的特定问题的 UI 文本。

## <a name="issue"></a>**问题**
*运行 Windows 10 的虚拟机配置为小于建议的 RAM 量，即 1 GB。*

## <a name="impact"></a>**影响**
*来宾操作系统和应用程序可能无法正常运行。可能没有足够的内存可同时运行多个应用程序。这会影响以下虚拟机：*
```
<list of virtual machines>
```
## <a name="resolution"></a>**解决方法**
*使用 Hyper-v 管理器将分配给此虚拟机的内存至少增加 1 GB。*

#### <a name="increase-the-memory-using-hyper-v-manager"></a>使用 Hyper-v 管理器增加内存

1.  打开 Hyper-V 管理器。 单击 **“开始”**，指向 **“管理工具”**，然后单击 **“Hyper-V 管理器”**。

2.  在结果窗格中的 " **虚拟机**" 下，选择要配置的虚拟机。 虚拟机的状态应列为 " **关**"。 如果不是，请右键单击该虚拟机，然后单击 " **关闭**"。

3.  在 **“操作”** 窗格中的虚拟机名称下，单击 **“设置”**。

4.  在导航窗格中，单击 " **内存**"。

5.  在 " **内存** " 页上，将 " **启动 RAM** " 设置为至少 1 GB，然后单击 **"确定"**。

### <a name="increase-the-memory-using-windows-powershell"></a>使用 Windows PowerShell 增加内存

1.  打开 Windows PowerShell。 从桌面 (，单击 " **开始** "，然后开始键入 **Windows PowerShell**。 ) 

2.  右键单击 " **Windows PowerShell** "，然后单击 " **以管理员身份运行**"。

3.  \<MyVM>将替换为虚拟机的名称后，运行此命令：

```
Set-VMMemory <MyVM> -StartupBytes 1GB
```

## <a name="see-also"></a>另请参阅
[Set-vmmemory](/powershell/module/hyper-v/set-vmmemory?view=win10-ps)