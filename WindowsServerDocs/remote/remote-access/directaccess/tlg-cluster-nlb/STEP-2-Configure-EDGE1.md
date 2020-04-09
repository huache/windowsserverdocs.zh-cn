---
title: 步骤2配置 EDGE1
description: 本主题是测试实验室指南的一部分-使用 windows Server 2016 的 Windows NLB 在群集中演示 DirectAccess
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 84457351-1ca7-4e7c-8e2c-53d55b1fcdc0
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8705e69debec2f0a19f5cc010ed5ca254cc56741
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80819310"
---
# <a name="step-2-configure-edge1"></a>步骤2配置 EDGE1

>适用于：Windows Server（半年频道）、Windows Server 2016

在 DirectAccess 服务器上执行以下过程：

## <a name="to-configure-directaccess-on-edge1"></a>在 EDGE1 上配置 DirectAccess
  
1.  在 "**开始**" 屏幕上，键入**ramgmtui.exe**，然后按 enter。 如果出现了 **“用户帐户控制”** 对话框，请确认其中显示的操作为所需的操作，然后单击 **“是”** 。  
  
2.  在远程访问管理控制台的左窗格中，单击 "**配置**"。  
  
3.  在控制台的中间窗格中，在 "**步骤2远程访问服务器**" 区域中，单击 "**编辑**"。  
  
4.  在**远程访问服务器安装**向导中，单击 "**前缀配置**"。 在 "**前缀配置**" 页上，在 "**分配给 DirectAccess 客户端计算机的 IPv6 前缀**" 中，输入**2001： db8：1：1000：：/59**，然后单击 "**下一步**"。  
  
5.  单击 **“完成”** 。  
  
6.  在控制台的中间窗格中，单击 "**完成**"。  
  
7.  在 "**远程访问查看**" 对话框中，检查配置设置，然后单击 "**应用**"。 在 **“应用远程访问设置向导设置”** 对话框中，单击 **“关闭”** 。
