---
title: 筛选 DNS 资源记录视图
description: 本主题是 Windows Server 2016 中的 IP 地址管理（IPAM）管理指南的一部分。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ipam
ms.topic: article
ms.assetid: 5b80294a-7325-476b-84eb-69f0d051e8b2
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 21e43751981b0b7b945c0c9404f6f93f36c48f16
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860660"
---
# <a name="filter-the-view-of-dns-resource-records"></a>筛选 DNS 资源记录视图

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题在 IPAM 客户端控制台中筛选 DNS 资源记录的视图。  
  
Administrators组成员或同等身份是执行此过程的最低要求。  
  
### <a name="to-filter-the-view-of-dns-resource-records"></a>筛选 DNS 资源记录的视图  
  
1.  在服务器管理器中，单击 " **IPAM**"。 IPAM 客户端控制台随即出现。  
  
2.  在导航窗格的 "**监视和管理**" 中，单击 " **DNS 区域**"。  导航窗格划分为一个上部导航窗格和一个较低的导航窗格。  
  
3.  在下部导航窗格中，单击 "**正向查找**"。 所有 IPAM 管理的 DNS 正向查找区域都显示在 "显示" 窗格搜索结果中。  
  
4.  单击要查看和筛选其记录的区域。  
  
5.  在 "显示" 窗格中，单击 "**当前视图**"，然后单击 "**资源记录**"。 区域的资源记录显示在显示窗格中。  
  
6.  在 "显示" 窗格中，单击 "**添加条件**"。  
  
    ![添加条件](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_01.jpg)  
  
7.  从下拉列表中选择一个条件。 例如，如果想要查看特定的记录类型，请单击 "**记录类型**"。  
  
    ![选择条件](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_02.jpg)  
  
8.  单击 **“添加”** 。  
  
    ![添加条件](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_03.jpg)  
  
9. **记录类型**作为搜索参数添加。 输入要查找的记录类型的文本。 例如，如果只想查看 SRV 记录，请键入**srv**。  
  
    ![指定要查找的记录的类型](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_04.jpg)  
  
10. 按 Enter。 DNS 资源记录根据你指定的条件和搜索短语进行筛选。  
  
    ![运行筛选器](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_05.jpg)  
  
## <a name="see-also"></a>另请参阅  
[DNS 资源记录管理](DNS-Resource-Record-Management.md)  
[管理 IPAM](Manage-IPAM.md)  
  


