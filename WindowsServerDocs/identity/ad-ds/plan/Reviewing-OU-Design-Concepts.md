---
ms.assetid: 41b56704-c6f9-4d29-af97-62123e300565
title: 查看 OU 设计概念
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: adb770769d9d79ca5f5d9a9a753ecb90914e2309
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938547"
---
# <a name="reviewing-ou-design-concepts"></a>查看 OU 设计概念

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

域 (OU) 结构的组织单位包括：

-   OU 层次结构的关系图

-   Ou 列表

-   对于每个 OU：

    -   OU 的用途

    -   控制 OU 或 OU 中的对象的用户或组的列表

    -   用户和组对 OU 中的对象拥有的控件类型

OU 层次结构不需要反映组织或组的部门层次结构。 Ou 是为特定目的而创建的，如委派管理、组策略的应用程序，或限制对象的可见性。

你可以设计你的 OU 结构，以便将管理委派给组织中需要自治来管理自己的资源和数据的个人或组。 Ou 表示管理边界，并使你能够控制数据管理员的授权范围。

例如，你可以创建一个名为 ResourceOU 的 OU，并使用它来存储属于某个组管理的文件和打印服务器的所有计算机帐户。 然后，你可以在 OU 上配置安全性，以便只有组中的数据管理员才有权访问该 OU。 这会阻止其他组中的数据管理员篡改文件和打印服务器帐户。

您可以通过为特定目的创建 Ou 的子树（例如组策略的应用程序）或限制受保护对象的可见性，使只有特定用户可以看到它们，从而进一步优化 OU 结构。 例如，如果需要将组策略应用到一组选择的用户或资源，则可以将这些用户或资源添加到 OU，然后将组策略应用到该 OU。 你还可以使用 OU 层次结构来启用更进一步的管理控制委派。

虽然 OU 结构中的级别数没有技术限制，但为了便于管理，我们建议你将 OU 结构限制为不超过10个级别的深度。 每个级别的 Ou 数量没有技术限制。 请注意，Active Directory 域服务 (AD DS) 启用的应用程序可能对可分辨名称中使用的字符数有限制 (即，目录中的对象的完整轻型目录访问协议 (LDAP) 或层次结构内的 OU 深度。

AD DS 中的 OU 结构不应向最终用户显示。 OU 结构是为服务管理员和数据管理员提供的管理工具，并且可以轻松地进行更改。 继续查看和更新你的 OU 结构设计，以反映你的管理结构中的更改并支持基于策略的管理。



