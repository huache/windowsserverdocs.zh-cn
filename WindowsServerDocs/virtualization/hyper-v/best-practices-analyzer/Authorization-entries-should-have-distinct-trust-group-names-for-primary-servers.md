---
title: 对于包含不属于同一信任组的虚拟机的主服务器，授权条目应具有不同的信任组名称
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8827a3a7-9f3c-4f51-826a-8e2ec43e01df
ms.date: 8/16/2016
ms.openlocfilehash: 984fa9233a433384cddae34af9a62bcf1e0204ca
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747102"
---
# <a name="authorization-entries-should-have-distinct-trust-group-names-for-primary-servers-with-virtual-machines-that-are-not-part-of-the-same-trust-group"></a>对于包含不属于同一信任组的虚拟机的主服务器，授权条目应具有不同的信任组名称

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
*服务器将从与虚拟机相同的复制标记相关联的授权列表中的任何服务器接受对副本虚拟机的复制请求。*

## <a name="impact"></a>**影响**
*从属于不同授权条目的主服务器接收复制的虚拟机可能存在隐私和安全问题。这会影响以下授权条目： \<list of authorization entries>*

## <a name="resolution"></a>**解决方法**
*使用不属于同一安全组的虚拟机的主服务器的授权条目中的不同标记。修改 Hyper-v 设置以配置复制标记。*



