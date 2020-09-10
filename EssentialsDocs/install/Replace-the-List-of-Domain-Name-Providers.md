---
title: 替换域名提供商列表
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 104d0412-2d77-4cd4-99f7-65a885522850
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 74509a7d64e718fe1d2b62f806306235e7d827e4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623359"
---
# <a name="replace-the-list-of-domain-name-providers"></a>替换域名提供商列表

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

可以通过完成以下任务来替换“设置域名”向导中显示的域名提供商列表：


-   [创建推荐服务文件](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)

-   [向引用计算机的注册表中添加项](Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)

-   [创建推荐服务文件](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)

-   [向引用计算机的注册表中添加项](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)


###  <a name="create-the-referral-service-files"></a><a name="BKMK_ReferralFiles"></a> 创建引用服务文件
 推荐服务管理工具将创建用于定义在“设置域名”向导中显示的域名提供商列表的文件集。 将为全球每个地区创建一个 XML 格式的文件，其中包含有关你在该工具中指定的域名提供商的信息。 该工具创建的文件必须位于可通过你在 Internet 上管理的安全链接 (HTTPS) 访问的文件夹中。

##### <a name="to-create-the-referral-files"></a>创建推荐文件

1.  打开推荐服务管理工具。

2.  单击“添加”。

3.  在“添加域名提供商”对话框中，输入域名提供商的名称。

4.  添加域名提供商所支持的顶级域。 此操作可通过单击 **“添加”**，输入顶级域标识符，然后选择所支持的区域来完成。 可以选择 **“所有区域”**。

5.  输入对域名提供商的说明。

6.  添加与域名提供商关联的所有网站的 URL。

7.  如果域名提供商有可用的徽标，请通过单击 **“更改徽标”** 添加徽标。

8.  单击“ **保存**”。

9. 为要在向导中列出的每个域名提供商重复步骤 2 至步骤 8。

10. 在添加所有域名提供商后，选择要在其中保存推荐文件的文件夹。 请注意，在选择文件夹时，必须通过 HTTPS 链接访问推荐文件。

11. 单击 **“在文件系统中生成文件”**。

###  <a name="add-an-entry-to-the-registry-on-the-reference-computer"></a><a name="BKMK_AddRegistry"></a> 向引用计算机上的注册表中添加项
 必须添加注册表项，以指定操作系统可在其中找到推荐服务文件的位置。

##### <a name="to-add-a-key-to-the-registry"></a>向注册表添加项

1.  在引用计算机上，单击 **“开始”**，输入 **regedit**，然后按 **Enter**。

2.  在左侧窗格中，依次展开 **“HKEY_LOCAL_MACHINE”**、**“SOFTWARE”**、**“Microsoft”**、**“Windows Server”**、**“Domain Managers”** 和 **“Providers”**。

3.  右键单击 **“E423C85D-6B1F-4583-95E0-449D8263BAC4”** 项，然后单击 **“字符串值”**。

4.  输入 **ReferralServerHttpsUri** 作为字符串的名称，然后按 **Enter**。

5.  右键单击右侧窗格中的新 **“ReferralServerHttpsUri”** 字符串，然后单击 **“修改”**。


6.  输入用于访问在[创建推荐服务文件](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)中创建的推荐文件的 HTTPS URL，然后单击 **“确定”**。

6.  输入用于访问在[创建推荐服务文件](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)中创建的推荐文件的 HTTPS URL，然后单击 **“确定”**。


~~~
> [!IMPORTANT]
>  A slash (/) is required at the end of the URL.
~~~

###  <a name="domain-name-status-issues"></a><a name="BKMK_ReplaceDomainNameProviders"></a> 域名状态问题
 如果合作伙伴添加域名提供者，并使用 Windows Server Essentials SDK 中 (API) 的应用程序编程接口为证书设置 Unknown、Failed 和 CertificateRequestNotSubmitted 状态，则客户会收到错误的消息和配置结果。 这是因为上述情况会得到例外处理，而不返回状态。

 下列域状态为失败结果，应作为错误进行报告：

- Failed

- PendingCustomerInterventionRequired

- PurchaseFailed

- DomainNotFound

- InRenewalCustomerInterventionRequired

- RenewalFailed

  下列域状态为成功结果，应作为成功信息进行报告：

- 就绪

- 挂起的

- InRenewal

## <a name="see-also"></a>另请参阅

 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)

