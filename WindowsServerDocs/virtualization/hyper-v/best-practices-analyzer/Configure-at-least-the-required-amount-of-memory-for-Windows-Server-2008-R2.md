---
title: 至少为运行 Windows Server 2008 R2 并为动态内存启用的虚拟机配置所需的内存量
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: db0bff4c-39fe-49c1-903a-1f2a0b0db891
ms.date: 8/16/2016
ms.openlocfilehash: eaafc5ba990e30880878c540642b32d2e81f63e0
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746932"
---
# <a name="configure-at-least-the-required-amount-of-memory-for-a-virtual-machine-running-windows-server-2008-r2-and-enabled-for-dynamic-memory"></a>至少为运行 Windows Server 2008 R2 并为动态内存启用的虚拟机配置所需的内存量

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*一台或多台虚拟机配置为使用小于 Windows Server 2008 R2 所需的内存量的动态内存。*

## <a name="impact"></a>影响
*以下虚拟机上的来宾操作系统可能无法运行或可能运行 unreliably：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器或 Windows PowerShell 将最小内存增加到至少 256 MB，将启动内存和最大内存增加到至少 512 MB。*

### <a name="increase-memory-using-hyper-v-manager"></a>使用 Hyper-v 管理器增加内存

1.  打开 Hyper-V 管理器。  (服务器管理器中，单击 "**工具**" "  >  **hyper-v 管理器**"。 ) 

2.  在虚拟机列表中，右键单击所需的虚拟机，然后单击 " **设置**"。

3.  在导航窗格中，单击 " **内存**"。

4.  将 **RAM** 改为至少 512 MB。

5.  在 " **动态内存**" 下，将 **最小 ram** 至少更改为 256 Mb，将 **最大 ram** 更改为 512 mb。

6.  单击“确定”。

### <a name="increase-memory-using-windows-powershell"></a>使用 Windows PowerShell 增加内存

1.  打开 Windows PowerShell。 从桌面 (，单击 " **开始** "，然后开始键入 **Windows PowerShell**。 ) 

2.  右键单击 " **Windows PowerShell** "，然后单击 " **以管理员身份运行**"。

3.  运行与下面类似的命令，将 MyVM 替换为虚拟机的名称，将替换为至少包含下面所示值的内存值。

```
Get-VM MyVM | Set-VMMemory -DynamicMemoryEnabled $True -MaximumBytes 512MB -MinimumBytes 256MB -StartupBytes 512MB
```



