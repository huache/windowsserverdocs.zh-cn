---
title: 设置电子邮件发现以订阅 RDS 源
description: 了解如何在 RDS 部署中设置电子邮件发现功能。
ms.author: chrimo
ms.date: 8/28/2020
ms.localizationpriority: medium
ms.topic: article
author: christianmontoya
ms.openlocfilehash: 71b892d95b15f02445ec7898a6c57f931bc4b501
ms.sourcegitcommit: 2b1a12c85acff137e5ac84cd0e62d8353fcdde31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89087460"
---
# <a name="set-up-email-discovery-to-subscribe-to-your-rds-feed"></a>设置电子邮件发现以订阅 RDS 源

你是否在将最终用户连接到他们已发布的 RDS 源时遇到过问题，原因是源 URL 中缺少一个字符，或者他们丢失了包含该 URL 的电子邮件？ 几乎所有远程桌面客户端应用程序都支持通过输入电子邮件地址来查找订阅，从而能够比以往更轻松地将用户连接到他们的 RemoteApp 和桌面。

在设置电子邮件发现之前，请执行以下操作：

- 确保你有权向与你的电子邮件关联的域添加 TXT 记录（例如，如果你的用户拥有 @contoso.com 电子邮件地址，那么，你需要有 contoso.com 域的权限）
- 创建 RD Web 源 URL (https://\<rdweb-dns-name\>.domain/RDWeb/Feed/webfeed.aspx)，例如 https://rdweb.contoso.com/RDWeb/Feed/webfeed.aspx)

>[!NOTE]
>如果你使用的是 Windows 虚拟桌面而不是远程桌面，则需要改用以下 URL：
>
>- 如果你使用的是 Windows 虚拟桌面（经典）：<https://rdweb.wvd.microsoft.com/api/feeddiscovery/webfedddiscovery.aspx>
>- 如果你使用的是 Windows 虚拟桌面：<https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery>

现在，按照以下步骤设置电子邮件发现：

1. 在浏览器中，连接到在其中注册了域的域名注册机构的网站。
2. 导航到已注册域的相应页面，可以在其中查看、添加和编辑 DNS 记录。
3. 输入具有以下属性的新 DNS 记录：
   - **主机:** _msradc
   - **文本：** \<RD Web Feed URL\>
   - **TTL:** 300

   DNS 记录字段的名称因域名注册机构而异，但此过程将生成名为 _msradc.\<domain_name\> 的 TXT 记录 （例如 _msradc.contoso.com），其值为完整的 RD Web 源。

就这么简单！ 现在，在设备上启动远程桌面应用程序并为自己订阅！