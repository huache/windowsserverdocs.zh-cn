---
ms.assetid: c20231dd-2b83-4494-9385-1172272e00d6
title: 确定是升级现有域还是部署新域
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 60f3dca9f4930fe9d1a717d741a818194a3db0f0
ms.sourcegitcommit: 11421f4005f9f3a3f6c0db95b1836d0f765a9fa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "81624275"
---
# <a name="determining-whether-to-upgrade-existing-domains-or-deploy-new-domains"></a>确定是升级现有域还是部署新域

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

设计中的每个域都是新域或现有升级域。 必须将尚未升级的现有域中的用户移到新域中。

在域之间移动帐户会影响最终用户。 在决定是将用户移动到新域还是升级现有域之前，请根据将用户移动到域中的成本评估新 AD DS 域的长期管理优势。

有关将 Active Directory 域升级到 Windows Server 2008 的详细信息，请参阅[将 Active Directory 域升级到 Windows server 2008 和 Windows server 2008 R2 AD DS 域](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731188(v=ws.10))。

若要详细了解如何在林中和林之间重新构建 AD DS 域，请参阅[ADMT 指南：迁移和重新构建 Active Directory 域](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc974332(v=ws.10))。

要使工作表可以帮助你记录新域和升级域的计划，请从[Windows Server 2003 部署工具包的作业帮助](https://microsoft.com/download/details.aspx?id=9608)下载 Job_Aids_Designing_and_Deploying_Directory_and_Security_Services .zip，并打开 "域计划" （DSSLOGI_5）。
