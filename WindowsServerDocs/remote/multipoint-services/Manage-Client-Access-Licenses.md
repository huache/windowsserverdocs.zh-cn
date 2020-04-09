---
title: 管理客户端访问许可证
description: 了解如何在 MultiPoint Services 中使用 Cal
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 675e089e-d841-401e-bba7-69f3929ef609
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 2981f22b2b85d90f4102c3a0b67e25901cb12395
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853540"
---
# <a name="manage-client-access-licenses"></a>管理客户端访问许可证
连接到 MultiPoint 服务系统的每个工作站（包括运行 MultiPoint 服务的计算机）都必须具有有效的按用户远程桌面*客户端访问许可证（CAL）* 。

如果使用的是工作站虚拟桌面，而不是物理工作站，则必须为每个工作站虚拟桌面安装 CAL。  
  
1.  为连接到 MultiPoint 服务计算机或服务器的每个工作站购买客户端许可证。 有关购买 Cal 的详细信息，请访问远程桌面授权文档。 

2.  从 "**开始**" 屏幕中，打开 " **MultiPoint 管理器**"。  
  
3.  单击 "**主页**" 选项卡，然后单击 "**添加客户端访问许可证**"。  这将打开 "CAL 授权" 管理工具。

## <a name="set-the-licensing-mode-manually"></a>手动设置授权模式
如果未正确配置，则将会提示 "MultiPoint 服务设置"，并通知有关宽限期已过期的通知。 请按照以下步骤设置授权模式：

1. 启动**本地组策略编辑器**（gpedit.msc）。

2. 在左窗格中，导航到 "**本地计算机策略-> 计算机配置-> 管理模板 > Windows 组件->** 远程桌面服务 > 远程桌面会话主机 >"。

3. 在右侧窗格中，右键单击 **"使用指定的远程桌面许可证服务器"** ，然后选择 "**编辑**"：
   - 在 "组策略编辑器" 对话框中，选择 "**已启用**"
   - 在 "**要使用的许可证服务器**" 字段中输入本地计算机名称。
   - 选择 **"确定"**
  
4. 在右侧窗格中，右键单击 **"设置远程桌面授权模式"** ，然后选择 "**编辑**"
   - 在 "组策略编辑器" 对话框中，选择 "**已启用**"
   - 为每个设备/每个用户设置**授权模式**
   - 选择 **"确定"** 

  
## <a name="see-also"></a>另请参阅  
[使用 MultiPoint 管理器管理系统任务](Manage-System-Tasks-Using-MultiPoint-Manager.md)
