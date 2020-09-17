---
title: 虚拟 SAN 应与物理主机总线适配器相关联
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 14bca69b-e779-4e90-b5c1-1b015625572f
ms.date: 8/16/2016
ms.openlocfilehash: d49cbedb76320f3c1967bfd6cfd1e9590fd8925d
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746372"
---
# <a name="a-virtual-san-should-be-associated-with-a-physical-host-bus-adapter"></a>虚拟 SAN 应与物理主机总线适配器相关联

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
*虚拟存储区域网络 (SAN) 已配置，但未与主机总线适配器 (HBA) 关联。*

## <a name="impact"></a>**影响**
*使用连接到配置错误的虚拟 SAN 的虚拟光纤通道适配器配置虚拟机时，该虚拟机将无法启动。这会影响以下虚拟 San：*


\<list of virtual SANs>


## <a name="resolution"></a>**解决方法**
*通过将虚拟 SAN 连接到主机总线适配器来重新配置它。*





