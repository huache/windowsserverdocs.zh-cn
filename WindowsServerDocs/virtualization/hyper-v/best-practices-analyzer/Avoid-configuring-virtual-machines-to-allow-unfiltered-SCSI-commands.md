---
title: 避免将虚拟机配置为允许未筛选的 SCSI 命令
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: dd4a3d78-a77f-451e-a383-d5cf45ea17cf
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 33c211073c74da334abb8b483fa36974216a1185
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87948580"
---
# <a name="avoid-configuring-virtual-machines-to-allow-unfiltered-scsi-commands"></a>避免将虚拟机配置为允许未筛选的 SCSI 命令

>适用于：Windows Server 2016



有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|操作|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*虚拟机配置为允许未筛选的 SCSI 命令。*

## <a name="impact"></a>影响

*绕过 SCSI 命令筛选会带来安全风险。仅当需要兼容来宾操作系统中运行的存储应用程序时，才应启用此配置。以下虚拟机配置为允许未筛选的 SCSI 命令：*

\<list of virtual machine names>

## <a name="resolution"></a>解决方法

*请与存储供应商联系以确定是否需要此配置。此外，如果管理操作系统或其他来宾操作系统被泄露或出现异常行为，请重新配置虚拟机以阻止这些命令。*



