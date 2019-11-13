---
title: 配置测试实验室的步骤
description: 本主题是测试实验室指南的一部分-演示带有 OTP 身份验证的 DirectAccess 和用于 Windows Server 2016 的 RSA SecurID
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a40183c-afd1-43ca-b306-05745640a37d
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ef5ce37983b8565fab8287eeaae7423be0c269f6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404727"
---
# <a name="steps-for-configuring-the-test-lab"></a>配置测试实验室的步骤

>适用于：Windows Server（半年频道）、Windows Server 2016

以下步骤介绍了如何配置远程访问基础结构、配置远程访问服务器和客户端，以及如何通过 Homenet 和 Internet 子网测试 DirectAccess 连接。  
  
在此测试实验室指南中，你将通过执行以下步骤来构建使用 OTP 环境的远程访问：  
  
-   [步骤1：完成 DirectAccess 配置](assetId:///4dbf877f-02fb-439b-907a-f5b3f1d8afa6)。 完成[测试实验室指南：演示带有混合 IPv4 和 IPv6 的 DirectAccess 单服务器安装程序](https://go.microsoft.com/fwlink/p/?LinkId=237004)中的所有步骤。  
  
-   [步骤2：配置 APP1](assetId:///c1bb590f-91d4-4ed5-bceb-b0e36eabd4ff)。 使用 OTP 证书模板配置 APP1 以供 EDGE1 使用。  
  
-   [步骤3：配置 DC1](assetId:///904a6edc-a771-45ed-9630-a34a680bb522)。 验证在 DC1 上定义的用户主体名称。  
  
-   [步骤7：安装和配置 RSA](assetId:///baa4c28c-add7-42e2-8afd-ccc7a559406a)。 安装和配置 RSA、RADIUS 和 OTP 服务器，并为 OTP 配置 EDGE1。  
  
-   [步骤11：验证 EDGE1 上的 OTP 运行状况](assetId:///3b397a4a-8478-47f2-a932-9e8e048c14ba)。 请确保远程访问服务器上的 OTP 状态为 "正常"。  
  
-   [步骤8：从 Homenet 子网测试 DirectAccess 连接](assetId:///ba1652a6-0692-4add-91ca-34a84956ba14)。 从 NAT 设备后面测试 DirectAccess OTP 功能。  
  
-   [步骤10：从 Internet 测试 DirectAccess 连接](assetId:///321149eb-5f23-4a0b-b8fb-1244540126e9)。 测试来自 Internet 的 DirectAccess 客户端连接。  
  
-   [步骤12：快照配置](assetId:///8a51ed3c-9c32-402f-85d1-617ce46845b4)。 完成测试实验室后，使用 OTP 配置拍摄工作 DirectAccess 的快照，以便稍后可以返回到测试其他方案。  
  


