---
title: 为 WEB1 在 DNS 中创建别名 (CNAME) 记录
description: 本主题是指导 802.1 X 有线和无线部署的 "部署服务器证书" 的一部分
manager: brianlic
ms.topic: article
ms.assetid: bfae23f0-ae12-486b-94fe-50a137e141a5
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 9a966ab2883e22173ecf3e64e87d2a4b7a9c57d2
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87995586"
---
# <a name="create-an-alias-cname-record-in-dns-for-web1"></a>\( \) 在 DNS 中为 WEB1 创建别名 CNAME 记录

>适用于：Windows Server（半年频道）、Windows Server 2016

可以使用此过程将 Web 服务器的别名规范名称 \( CNAME \) 资源记录添加到域控制器上 DNS 中的某个区域。 对于 CNAME 记录，你可以使用多个名称来指向单个主机，这样就可以轻松地在 \( 同一台计算机上同时托管文件传输协议的 FTP \) 服务器和 Web 服务器。

因此，你可以使用 Web 服务器来承载证书颁发机构 CA 的证书吊销列表 \( CRL， \) 还可以 \( \) 执行其他服务，如 FTP 或 Web 服务器。

执行此过程时，请将**Alias 名称**和其他变量替换为适用于你的部署的值。

若要执行此过程，您必须是**Domain Admins**的成员。

## <a name="to-add-an-alias-cname-resource-record-to-a-zone"></a>将别名 \( CNAME \) 资源记录添加到区域

>[!NOTE]
>若要使用 Windows PowerShell 执行此过程，请参阅[DnsServerResourceRecordCName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname?view=winserver2012r2-ps)。

1.  在 DC1 上的服务器管理器中，单击 "**工具**"，然后单击 " **DNS**"。 此时将打开 DNS 管理器 Microsoft 管理控制台 (MMC) 。

2.  在控制台树中，双击 "**正向查找区域**"，右键单击要在其中添加别名资源记录的正向查找区域，然后单击 "**新建别名 \( CNAME \) **"。 此时将打开 "**新建资源记录**" 对话框。

3.  在 "**别名**" 中，键入别名 **。**

4.  为 "**别名**" 键入值时，对话框中的**完全限定域名 \( FQDN \) **将自动填充。 例如，如果你的别名为 "pki"，而你的域为 corp.contoso.com，则会自动为你填充值**pki.corp.contoso.com** 。

5.  在 " ** \( \) 目标主机的完全限定的域名 fqdn**" 中，键入 Web 服务器的 fqdn。 例如，如果你的 Web 服务器名为 WEB1，并且你的域为 corp.contoso.com，则键入**WEB1.corp.contoso.com**。

6.  单击 **"确定"** 将新记录添加到区域。