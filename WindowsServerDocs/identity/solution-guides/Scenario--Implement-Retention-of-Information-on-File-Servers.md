---
ms.assetid: 81c55015-82e5-4ba1-b15e-cc7b49af28fc
title: 方案实现文件服务器上信息的保留
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 479aaaf96eab094f3ba7556c0c0416c9915f4620
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87940209"
---
# <a name="scenario-implement-retention-of-information-on-file-servers"></a>方案：实现文件服务器上信息的保留

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

保留期是文档过期前应保存的时间量。 组织不同，保留期可能也不相同。 可以将文件夹中的文件分类为具有短、中或长保留期，然后为每个保留期分配时间范围。 你可能想要通过将文件合法保留来无限期保留。

## <a name="scenario-description"></a><a name="BKMK_OVER"></a>方案描述
文件分类基础结构和文件服务器资源管理器使用文件管理任务和文件分类，将保留期应用到一系列文件上。 可给文件夹分配一个保留期，然后使用文件管理任务配置分配的保留期的持续时间。 当文件夹中的文件将要过期时，文件所有者会收到一封通知邮件。 也可将文件分类为合法保留，这样文件管理任务就不会使文件过期。

可以在[文件服务器信息保留方案](assetId:///edf13190-7077-455a-ac01-f534064a9e0c)中查找有关配置保留的计划信息。

可以在部署中找到用于对文件进行法律封存分类的步骤，以及在部署中配置保留期， [&#40;演示步骤&#41;](Deploy-Implementing-Retention-of-Information-on-File-Servers--Demonstration-Steps-.md)。

> [!NOTE]
> 本方案仅讨论如何手动将文档归类为合法保留。 但是，在 Windows Server 2012 中，可以自动将文档归类为合法保留。 实现此目的的一个方法是创建 Windows PowerShell 分类器，它可以将文件所有者和合法保留下的用户帐户列表进行比较。 如果文件所有者是用户帐户列表的一部分，则将该文件归类为合法保留。

## <a name="in-this-scenario"></a>本方案内容
本方案是动态访问控制方案的一部分。 有关动态访问控制的其他信息，请参阅：

-   [动态访问控制：方案概述](Dynamic-Access-Control--Scenario-Overview.md)

## <a name="features-included-in-this-scenario"></a><a name="BKMK_NEW"></a>本方案中所含的功能
下表列出了本方案的部分功能并说明了支持该方案的工作原理。

|功能|如何支持本方案|
|-----------|---------------------------------|
|[File Server Resource Manager Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831701(v=ws.11))|文件分类基础结构是包含在文件服务器资源管理器中的功能。|
|[文件和存储服务概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831487(v=ws.11))|文件服务器资源管理器是包含在文件服务服务器角色中的功能。|


