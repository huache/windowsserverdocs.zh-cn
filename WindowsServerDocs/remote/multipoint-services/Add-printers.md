---
title: 添加打印机
description: 为 MultiPoint 服务用户添加打印机。
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: e1f6d3ca-8caf-4aa0-b0ea-93cdfd3f3f37
author: evaseydl
manager: scottman
ms.author: evas
ms.date: 08/04/2016
ms.openlocfilehash: 7be399a73ee37413e01ef714cfd02d4e8750ab79
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856080"
---
# <a name="add-printers"></a>添加打印机
使用本主题中的过程来使本地打印机对 MultiPoint 服务系统上的所有用户可用。  
  
> [!NOTE]  
> 如果使用的是带 MultiPoint 服务的域帐户，用户可以使用其工作站的任何网络打印机。  
  
1.  将打印机连接到 Multipoint 服务器。  
  
2.  将打印机配置为共享打印机：  
  
    1.  以管理员身份登录到 MultiPoint 服务器计算机。  
  
    2.  从 **“开始”** 屏幕打开 **“控制面板”** 。  
  
    3.  在控制面板中，单击 "**硬件**"，然后单击 "**设备和打印机**"。  
  
    4.  在 "**打印机和传真**" 下，右键单击打印机，然后单击 "**打印机属性**"。  
  
    5.  单击 "**共享**" 选项卡。  
  
    6.  单击 "**共享这台打印机**"，为打印机指定共享名称，然后单击 **"确定"** 。  
  
登录到连接到 Multipoint 服务计算机的任何工作站的用户都可以查看和使用打印机。 