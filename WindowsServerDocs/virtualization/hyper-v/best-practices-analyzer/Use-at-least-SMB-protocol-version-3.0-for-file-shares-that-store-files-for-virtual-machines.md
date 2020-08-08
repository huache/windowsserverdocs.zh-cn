---
title: 为虚拟机存储文件的文件共享至少使用 SMB 协议版本3.0。
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 4bb832b8-f1aa-4c1f-a0f2-324dd53553ea
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: b2393e2aa0418758ff59c527cef6f38a0c8b8402
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87948384"
---
# <a name="use-at-least-smb-protocol-version-30-for-file-shares-that-store-files-for-virtual-machines"></a>为虚拟机存储文件的文件共享至少使用 SMB 协议版本3.0。

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*虚拟机文件或虚拟硬盘文件存储在不支持 SMB 协议版本3.0 的文件共享上。*

## <a name="impact"></a>**影响**
*Microsoft 不支持此配置。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*将文件移动到至少使用 SMB 协议版本3.0 的文件共享中。*



