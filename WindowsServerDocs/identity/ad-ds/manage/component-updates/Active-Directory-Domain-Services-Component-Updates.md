---
title: Active Directory 域服务组件更新
description: 本文档介绍 Windows Server 2012 R2 的 AD DS 组件更新
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 09/08/2017
ms.topic: article
ms.prod: windows-server
ms.assetid: a3a91034-a4da-4ad7-93f8-0cd2ec3e7824
ms.technology: identity-adds
ms.openlocfilehash: 0dfb108067bee1a5f276963116e2a72b99f6aec2
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961119"
---
# <a name="active-directory-domain-services-component-updates"></a>Active Directory 域服务组件更新

>适用于： Windows Server 2016、Windows Server 2012 R2

本模块介绍在“目录服务和标识”空间中收到较少更新的组件。  


| 关于作者 |
|------------------|
|   **作者：**    |
|     **个人简历：**     |
| **供稿人** |
|  **审阅者**   |

> [!NOTE]  
> 本内容由 Microsoft 客户支持工程师编写，适用于正在查找比 TechNet 主题通常提供的内容更深入的有关 Windows Server 2012 R2 中的功能和解决方案的技术说明的有经验管理员和系统架构师。 但是，它未经过相同的编辑审批，因此某些语言可能看起来不如通常在 TechNet 上找到的内容那么精练。  

### <a name="what-you-will-learn"></a>学习内容  
完成本模块后，你将能够：  

-   说明 Windows Server 2012 R2 在目录服务和标识技术方面所做的组件更新  

    -   [SPN 和 UPN 唯一性](../../../ad-ds/manage/component-updates/SPN-and-UPN-uniqueness.md)  

    -   [Winlogon 自动重新启动登录 &#40;ARSO&#41;](../../../ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md)  

    -   [TPM 密钥证明](../../../ad-ds/manage/component-updates/TPM-Key-Attestation.md)  

    -   [CA 备份和还原 Windows PowerShell cmdlet](../../../ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md)  

    -   [命令行进程审核](../../../ad-ds/manage/component-updates/Command-line-process-auditing.md)  

    -   [凭据保护和管理](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn408190(v=ws.11))  

    -   [目录服务组件更新](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md)  

        -   [域和林功能级别](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_FL)  

        -   [弃用 NTFRS](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_NTFRS)  

        -   [LDAP 查询优化程序更改](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_LDAPQuery)  

        -   [1644 事件改进](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_1644)  

        -   [Active Directory 复制吞吐量改进](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_ADRepl)  
