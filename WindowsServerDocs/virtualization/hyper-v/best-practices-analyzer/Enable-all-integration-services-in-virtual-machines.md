---
title: 启用虚拟机中的所有集成服务
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 16e202ad-3795-40c9-8176-7ca319e56d26
ms.date: 8/16/2016
ms.openlocfilehash: ca614074035678f50dd55b82864d989b789e61fb
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746872"
---
# <a name="enable-all-integration-services-in-virtual-machines"></a>启用虚拟机中的所有集成服务

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

*一个或多个集成服务已禁用或在虚拟机中不工作。*

## <a name="impact"></a>影响

*对于下列虚拟机，服务或集成功能可能无法正常运行：*

\<list of virtual machine names>

## <a name="resolution"></a>解决方法

*使用 "服务" 管理单元或 sc config 命令行工具验证是否已将服务配置为自动启动且不会停止。*

#### <a name="to-configure-how-a-service-is-started-using-the-services-snap-in"></a>使用 "服务" 管理单元配置服务的启动方式

1.  使用远程桌面服务或虚拟机连接连接到虚拟机，并登录到来宾操作系统。

2.  打开服务。  (单击 " **开始**"，在 " **开始搜索** " 框中单击，键入 **services.msc**，然后按 enter。 ) 

3.  在详细信息窗格中，右键单击要配置的服务，然后单击 " **属性**"。

4.  在 " **常规** " 选项卡上，在 " **启动** 类型" 中单击 " **自动**"。

#### <a name="to-configure-how-a-service-is-started-using-sc-config"></a>使用 SC Config 配置服务的启动方式

1.  打开 Windows PowerShell。 从桌面 (，单击 " **开始** "，然后开始键入 **Windows PowerShell**。 ) 

2.  右键单击 " **Windows PowerShell** "，然后单击 " **以管理员身份运行**"。

3.  将 <服务名称> 替换为服务的名称，然后键入：

    ```
    sc config <service-name> start=auto
    ```



