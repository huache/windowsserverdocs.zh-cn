---
title: 建议复制基于证书的身份验证
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: d931cc57-414f-4bdf-9ebd-08fd5e22b19d
ms.date: 8/16/2016
ms.openlocfilehash: 3ef11472c042e19de9f7ee52ea5958ca0bf6e44b
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745852"
---
# <a name="certificate-based-authentication-is-recommended-for-replication"></a>建议复制基于证书的身份验证

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*为 Kerberos 身份验证配置了一个或多个为复制选择的虚拟机。*

## <a name="impact"></a>**影响**
*从主服务器到复制服务器的复制网络流量未加密。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*如果使用另一种方法执行加密，则可以忽略此情况。否则，请修改虚拟机设置以选择基于证书的身份验证。*



