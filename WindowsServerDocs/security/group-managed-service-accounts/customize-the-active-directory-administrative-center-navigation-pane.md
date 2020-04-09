---
title: 自定义 Active Directory 管理中心导航窗格
ms.prod: windows-server
description: Windows Server 安全
ms.assetid: c9933d16-e153-435a-b5b7-3e594db42d5c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 0053fc4e4f3e22a8fd98e242e38fc7c4e2002867
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857000"
---
# <a name="customize-the-active-directory-administrative-center-navigation-pane"></a>自定义 Active Directory 管理中心导航窗格

>适用于：Windows Server（半年频道）、Windows Server 2016

  您可以使用树视图浏览 Active Directory 管理中心导航窗格，该视图与 "Active Directory 用户和计算机" 控制台树或通过使用列表视图相同。

 无论你使用树视图还是列表视图，你都可以随时通过从本地域或任何外 \(域添加不同容器来自定义你的 Active Directory 管理中心导航窗格，而此域不是与本地域\) 作为单独节点的 "导航" 窗格相同的域。 自定义 Active Directory 管理中心导航窗格可以更快地访问 Active Directory 对象。 有关详细信息，请参阅[在 Active Directory 管理中心中管理不同的域](manage-different-domains-in-active-directory-administrative-center.md)。

 此外，若要进一步自定义导航窗格，可以重命名或删除这些手动添加的导航窗格节点，创建这些节点的副本，或者在导航窗格中向上或向下移动它们。

> [!NOTE]
>  无法自定义默认的本地域节点。

### <a name="to-customize-the-active-directory-administrative-center-navigation-pane"></a>自定义 Active Directory 管理中心导航窗格

1. 在 Active Directory 管理中心导航窗格中，右键单击要修改的节点\-。 可以修改节点的位置和名称，还可以创建节点的副本。

2. 单击以下命令之一：

   -   **重命名**

   -   **创建重复节点**

   -   **删除**

   -   **上移**

   -   **向下移动**

   通过使用列表视图，你可以利用最近使用的 \(MRU\) 列表。 当你在此导航节点中访问至少一个容器时，MRU 列表会自动显示在导航节点下。 还可以通过展开 "Active Directory 管理中心" 窗口顶部的痕迹导航栏来查看当前 MRU 列表。 MRU 列表始终包含在特定导航节点中访问过的最后三个容器。 在每次选择特定容器时，该容器会被添加至 MRU 列表的顶部，并从 MRU 列表中删除最后一个容器。

  

