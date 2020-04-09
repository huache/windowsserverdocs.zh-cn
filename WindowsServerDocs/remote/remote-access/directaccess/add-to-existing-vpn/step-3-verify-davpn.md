---
title: 步骤3验证部署
description: 本主题是将 DirectAccess 添加到 Windows Server 2016 现有远程访问（VPN）部署的指南的一部分
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 43ac612e-2e77-418c-8171-ebb2086b7cb6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: b187d017a3cf2865a92d95a8ae93bec11ff457f0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859530"
---
# <a name="step-3-verify-the-deployment"></a>步骤3验证部署

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍如何验证是否已正确配置 DirectAccess 部署。  
  
### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>验证通过 DirectAccess 对内部资源进行的访问  
  
1.  将 DirectAccess 客户端计算机连接到公司网络并获取组策略。  
  
2.  单击通知区域中的“网络连接” 图标以访问 DA 媒体管理器。  
  
3.  单击“DirectAccess 连接”，你会看到状态是“本地连接”。  
  
4.  将客户端计算机连接到外部网络并尝试访问内部资源。  
  
    你应能够访问所有公司资源。  
  


