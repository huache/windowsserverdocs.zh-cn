---
title: 在文件共享上启用 BranchCache（可选）
description: 本主题是适用于 Windows Server 2016 的 BranchCache 部署指南的一部分，它演示了如何在分布式和托管缓存模式下部署 BranchCache，以优化分支机构中的 WAN 带宽使用情况
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9c465a9e-c504-44ec-9ebc-4e06ba54db30
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 501fd1b1ac3b0bc7a0767ec57502ba18a8ee76e4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861080"
---
# <a name="enable-branchcache-on-a-file-share-optional"></a>在文件共享上启用 BranchCache（可选）

>适用于：Windows Server（半年频道）、Windows Server 2016

可以使用此过程在文件共享上启用 BranchCache。  
  
> [!IMPORTANT]  
> 如果将哈希发布设置配置为 "**允许对所有共享文件夹进行哈希发布**"，则不需要执行此过程。  
  
**Administrators**中的成员身份或同等身份是执行此过程所需的最低要求。  
  
### <a name="to-enable-branchcache-on-a-file-share"></a>在文件共享上启用 BranchCache  
  
1.  打开 Windows PowerShell，键入 **mmc**，然后按 Enter。 Microsoft 管理控制台 (MMC) 会打开。  
  
2.  在 MMC 的“文件”菜单上，单击“添加/删除管理单元”。 "**添加或删除管理单元**" 对话框将打开。  
  
3.  在 "**添加或删除管理单元**" 的 "**可用管理单元**" 中，双击 "**共享文件夹**"。 共享文件夹向导将打开，并选中 "本地计算机" 对象。 配置所需的视图，单击 "**完成**"，然后单击 **"确定"** 。  
  
4.  双击 "**共享文件夹（本地）** "，然后单击 "**共享**"。  
  
5.  在详细信息窗格中，右键单击某个共享，然后单击 "**属性**"。 此时将打开共享的 "**属性**" 对话框。  
  
6.  在 "**属性**" 对话框的 "**常规**" 选项卡上，单击 "**脱机设置**"。 "**脱机设置**" 对话框将打开。  
  
7.  请确保选中 **"仅用户指定的文件和程序可以脱机使用**"，然后单击 "**启用 BranchCache**"。  
  
8.  单击“确定”两次 。  
  

