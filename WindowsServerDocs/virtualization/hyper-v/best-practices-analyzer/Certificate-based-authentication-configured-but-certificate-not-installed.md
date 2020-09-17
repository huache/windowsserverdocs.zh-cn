---
title: 配置了基于证书的身份验证，但未在副本服务器或故障转移群集节点上安装指定的证书
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 4cabbce3-9367-4ddc-a108-1e5e1ab2bcff
ms.date: 8/16/2016
ms.openlocfilehash: 545a51f110a264e1fb456039362e373a51bcb2f8
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745862"
---
# <a name="certificate-based-authentication-is-configured-but-the-specified-certificate-is-not-installed-on-the-replica-server-or-failover-cluster-nodes"></a>配置了基于证书的身份验证，但未在副本服务器或故障转移群集节点上安装指定的证书

>适用于：Windows Server 2016



有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*已将 Hyper-v 副本配置为用于提供基于证书的复制的安全证书未安装在副本服务器上 (或) 任何故障转移群集节点。*

## <a name="impact"></a>影响

*发生群集故障转移或移动到其他节点时，如果新节点还没有安装适当的证书，Hyper-v 复制将暂停。这会影响以下节点：*

\<list of nodes>

## <a name="resolution"></a>解决方法

*在副本服务器上安装配置的证书 (以及故障转移群集中的所有关联节点（如果) 有）。*



