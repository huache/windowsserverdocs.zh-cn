---
ms.assetid: 0fd7b6aa-3e50-45a3-a3a6-56982844363e
title: 事件 ID 2088-复制成功时出现 DNS 查找失败
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 9dbb7debbca8d1625ebe975a051ed8b607d1ddd0
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87943282"
---
# <a name="event-id-2088-dns-lookup-failure-occurred-with-replication-success"></a>事件 ID 2088：DNS 查找失败但复制成功

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

当运行 Windows Server 2003 Service Pack 1 (SP1) 的目标域控制器在目录服务事件日志中收到事件 ID 2088 时，会尝试将 (别名中的全局唯一标识符 (GUID) 解析为源域控制器的 IP 地址失败。 但是，目标域控制器尝试使用完全限定的域名 (FQDN) 或源域控制器的 NetBIOS 名称来解析名称并成功。 尽管复制成功，但应诊断和解决域名系统 (DNS) 问题。

下面是事件文本的示例：

```
Log Name: Directory Service
Source: Microsoft-Windows-ActiveDirectory_DomainService
Date: 3/15/2008  9:20:11 AM
Event ID: 2088
Task Category: DS RPC Client
Level: Warning
Keywords: Classic
User: ANONYMOUS LOGON
Computer: DC3.contoso.com
Description:
Active Directory could not use DNS to resolve the IP address of the source domain controller listed below. To maintain the consistency of Security groups, group policy, users and computers and their passwords, Active Directory Domain Services successfully replicated using the NetBIOS or fully qualified computer name of the source domain controller.
```

无效的 DNS 配置可能会影响成员计算机、域控制器或此 Active Directory 域服务林中的应用程序服务器上的其他重要操作，包括登录身份验证或对网络资源的访问权限。

应该立即解决此 DNS 配置错误，使此域控制器可以使用 DNS 解析源域控制器的 IP 地址。

备用服务器名称： DC1 失败的 DNS 主机名： 4a8717eb-8e58-456c-995a-c92e4add7e8e _msdcs。

注意：默认情况下，在任何给定的12小时时间段内只显示最多10个 DNS 故障，即使出现了10个以上的失败。  若要记录所有单独的故障事件，请将以下诊断注册表值设置为1：

注册表路径： HKLM\System\CurrentControlSet\Services\NTDS\Diagnostics\22 DS RPC 客户端

用户操作：

1) 如果源域控制器不再运行，或者已使用其他计算机名称或 NTDSDSA 对象 GUID 重新安装了其操作系统，请使用 MSKB 文章216498中所述的步骤，ntdsutil.exe 删除源域控制器的元数据。

2) 键入 "net view \\ <source DC name> " 或 "ping"，确认源域控制器正在运行 Active Directory 并且可在网络上访问 <source DC name> 。

3) 验证源域控制器是否正在对 DNS 服务使用有效的 DNS 服务器，以及是否已正确注册源域控制器的主机记录和 CNAME 记录，并使用上提供的 DCDIAG.EXE 的 DNS 增强版本<https://www.microsoft.com/dns>

dcdiag/test： dns

4) 通过在目标域控制器的控制台上运行 DCDIAG.EXE 命令的 DNS 增强版，验证此目标域控制器是否对 DNS 服务使用有效的 dns 服务器，如下所示：

dcdiag/test： dns

5) 有关 DNS 错误故障的进一步分析，请参阅 KB 824449：<https://support.microsoft.com/?kbid=824449>

其他数据错误值：11004请求的名称有效，但找 </code> 不到请求类型的数据</introduction>
  <section>
    <title>诊断</title>
    <content>
      <para>在 dns 中使用别名 (CNAME) 资源记录来解析源域控制器名称失败的原因可能是 dns 的错误配置或 DNS 数据传播延迟。</para>
    </content>
  </section>
  <section>
    <title>解决方法</title>
    <content>
      <para>按照事件 ID 2087 中所述继续进行 DNS 测试 &quot; <link xlink:href="85b1d179-f53e-4f95-b0b8-5b1c096a8076">： dns 查找失败导致复制失败</link>。&quot;</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>
