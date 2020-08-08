---
title: 文件屏蔽管理
description: 本文介绍了如何创建文件屏蔽、生成通知、定义文件屏蔽模板和创建文件屏蔽异常
ms.date: 7/7/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: c189386ac340e9362c8774340732f8689f17effe
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87957434"
---
# <a name="file-screening-management"></a>文件屏蔽管理

> 适用于： Windows Server 2019，Windows Server 2016，Windows Server (半年通道) ，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2

在文件服务器资源管理器 MMC 管理单元的**文件屏蔽管理**节点上，可以执行以下任务：

-   创建文件屏蔽以控制用户可以保存的文件类型，以及在用户尝试保存未授权文件时生成通知。
-   定义可被应用到新卷或文件夹或可在组织中使用的文件屏蔽模板。
-   创建可扩展文件屏蔽规则灵活性的文件屏蔽异常。

例如，你可以：

-   确保服务器的个人文件夹中未保存任何音乐文件，但可以允许存储支持法律权利管理或符合公司政策的特定类型的媒体文件。 在相同的情况下，你可能希望为公司副总裁提供特殊权限以允许其在个人文件夹中存储任何类型的文件。
-   实施屏蔽过程以在可执行文件被保存到共享文件夹时以电子邮件方式通知你（包括保存文件的用户信息和文件的确切位置），这样你就可以采取合适的预防措施。

本节包括下列主题：

-   [定义用于屏蔽的文件组](define-file-groups-for-screening.md)
-   [创建文件屏蔽](create-file-screen.md)
-   [创建文件屏蔽例外](create-file-screen-exception.md)
-   [创建文件屏蔽模板](create-file-screen-template.md)
-   [编辑文件屏蔽模板属性](edit-file-screen-template-properties.md)

> [!Note]
> 若要设置电子邮件通知和特定的报告功能，必须首先配置文件服务器资源管理器常规选项。

## <a name="additional-references"></a>其他参考

-   [设置文件服务器资源管理器选项](setting-file-server-resource-manager-options.md)


