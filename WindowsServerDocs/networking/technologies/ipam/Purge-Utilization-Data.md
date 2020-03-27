---
title: 清除利用率数据
description: 本主题是 Windows Server 2016 中的 IP 地址管理（IPAM）管理指南的一部分。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45cada9e-69b9-43df-b6f5-6d3942435809
ms.author: lizross
author: eross-msft
ms.openlocfilehash: a8542e643a9c4d33acad18523fd34eed8926413d
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316777"
---
# <a name="purge-utilization-data"></a>清除利用率数据

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题来了解如何从 IPAM 数据库中删除利用率数据。  

若要执行此过程，你必须是**IPAM 管理员**组、本地计算机**管理员**组的成员或同等身份。

## <a name="to-purge-the-ipam-database"></a>清除 IPAM 数据库  
1. 打开服务器管理器，然后浏览到 IPAM 客户端接口。
2. 浏览到以下位置之一： **Ip 地址块**、 **ip 地址清单**或**ip 地址范围组**。  
3. 单击 "**任务**"，然后单击 "**清除利用率数据**"。 此时将打开 "**清除利用率数据**" 对话框。
4. 在 "**清除或之前的所有利用率数据**" 中，单击 "**选择日期**"。
5. 选择要删除在该日期和之前的所有数据库记录的日期。
6. 单击“确定”。 IPAM 会删除你指定的所有记录。
