---
title: 编辑 DNS 区域
description: 本主题是 Windows Server 2016 中的 IP 地址管理 (IPAM) 管理指南的一部分。
manager: brianlic
ms.topic: article
ms.assetid: a35164e1-11ad-47c8-9843-580d30c70d07
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 4ee5416bfe416759bc4a190575eb63534ec9b76d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971794"
---
# <a name="edit-a-dns-zone"></a>编辑 DNS 区域

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用本主题在 IPAM 客户端控制台中编辑 DNS 区域。

Administrators**** 组成员或同等身份是执行此过程的最低要求。

### <a name="to-edit-a-dns-zone"></a>编辑 DNS 区域

1.  在服务器管理器中，单击 " **IPAM**"。 IPAM 客户端控制台随即出现。

2.  在导航窗格的 "**监视和管理**" 中，单击 " **DNS 区域**"。 导航窗格划分为一个上部导航窗格和一个较低的导航窗格。

3.  在下部导航窗格中，选择以下选项之一：

    -   正向查找

    -   IPv4 反向查找

    -   IPv6 反向查找

4.  例如，选择 "IPv4 反向查找"。

    ![选择区域类型](../../media/Edit-a-DNS-Zone/ipam_EditZone_01.jpg)

5.  在 "显示" 窗格中，右键单击要编辑的区域，然后单击 "**编辑 DNS 区域**"。

    ![编辑 DNS 区域](../../media/Edit-a-DNS-Zone/ipam_EditZone_02.jpg)

6.  此时将打开 "**编辑 DNS 区域**" 对话框，其中选择了 "**常规**" 页。 如果需要，编辑常规区域属性： " **DNS 服务器**"、"**区域类别**" 和 "**区域类型**"，然后单击 "**应用**"，或者，如果编辑完成，请单击 **"确定"**。

    ![编辑区域属性并保存](../../media/Edit-a-DNS-Zone/ipam_EditZone_03a.jpg)

7.  在 "**编辑 DNS 区域**" 对话框中，单击 "**高级**"。 "**高级**区域属性" 页将打开。 如果需要，编辑要更改的属性，然后单击 "**应用**"，或者在编辑完成后单击 **"确定"**。

    ![编辑高级区域属性](../../media/Edit-a-DNS-Zone/ipam_EditZone_04a.jpg)

8.  如果需要，请选择 "其他区域属性" 页名称 (名称服务器、SOA、区域传输) 、进行编辑，然后单击 "**应用** **" 或 "确定"**。 若要查看区域的所有编辑，请单击 "**摘要**"，然后单击 **"确定"**。

## <a name="see-also"></a>另请参阅
[DNS 区域管理](DNS-Zone-Management.md) 
[管理 IPAM](Manage-IPAM.md)



