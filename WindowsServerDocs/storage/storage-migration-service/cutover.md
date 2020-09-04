---
title: 在存储迁移服务中切换的工作方式
description: 存储迁移服务中切换阶段的摘要和详细信息
author: t-chrche
ms.author: t-chrche
manager: nedpyle
ms.date: 08/31/2020
ms.topic: article
ms.openlocfilehash: 985fd14b7791d28246b8e9186ca83216df734875
ms.sourcegitcommit: a640c2d7f2d21d7cd10a9be4496e1574e5e955f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89448915"
---
# <a name="how-cutover-works-in-storage-migration-service"></a>在存储迁移服务中切换的工作方式

转换是将源计算机的网络标识移动到目标计算机的迁移阶段。 切换后，源计算机仍将包含与以前相同的文件，但不会提供给用户和应用程序使用。

## <a name="summary"></a>总结

![转换配置屏幕快照 ](media/cutover/cutover_configuration.png)
 __图1：存储迁移服务转换配置__

在转换开始之前，你将提供要从源计算机转移到目标计算机所需的网络配置信息。 你还可以为源计算机选择新的唯一名称，或让存储迁移服务创建一个随机名称。

然后，存储迁移服务会执行以下步骤，将源计算机剪切到目标计算机：

1. 我们连接到源和目标计算机。 它们应该都已启用以下防火墙规则：
    *  (SMB 的文件和打印机共享-在) 中，TCP 端口445
    * Netlogon 服务 (NP-IN-In) ，TCP 端口445
    *  (DCOM Windows Management Instrumentation) TCP 端口135
    *  (WMI Windows Management Instrumentation) 、TCP、任意端口

2. 在 Active Directory 域服务中设置目标计算机上的安全权限，以匹配源计算机的权限。

3. 我们会在源计算机上创建一个临时的本地用户帐户。 如果计算机已加入域，则帐户用户名为 "MsftSmsStorMigratSvc"。 我们禁用源计算机上的 [本地帐户令牌筛选器策略](https://support.microsoft.com/help/951016/description-of-user-account-control-and-remote-restrictions-in-windows) 以允许帐户通过，然后连接到源计算机。 我们创建了此临时帐户，以便以后重新启动并从域中删除源计算机时，仍可以访问源计算机。

4. 在目标计算机上重复上述步骤。

5. 我们从域中删除源计算机，以释放其 Active Directory 帐户，目的计算机将在以后接管该帐户。

6. 映射源计算机上的网络接口，并重命名源计算机。

7. 我们将源计算机添加回该域。 源计算机现在具有新的标识，可用于管理员，而不是用户和应用。

8. 在源计算机上，删除任何延迟备用计算机名称，删除我们创建的临时本地帐户，然后重新启用本地帐户令牌筛选器策略。

9. 我们从域中删除目标计算机。

10. 我们将目标计算机上的 IP 地址替换为源提供的 IP 信息，然后将目标计算机重命名为源计算机的原始名称。

11. 我们将目标计算机加入域。 联接后，它将使用源计算机的原始 Active Directory 计算机帐户。 这会保留组成员身份和安全 Acl。 目标计算机现在具有源计算机的标识。

12. 在目标计算机上，删除任何延迟备用计算机名称，删除我们创建的临时本地帐户，然后重新启用本地帐户令牌筛选器策略，完成转换。

在转换完成后，目标计算机将获取源计算机的标识，然后就可以解除源计算机的授权。

## <a name="detailed-stages"></a>详细阶段

![切换阶段说明屏幕截图 ](media/cutover/cutover_stage_description.png)
 __图2：存储迁移服务显示切换阶段说明__

您可以通过显示的每个阶段的说明跟踪转换进度，如下图所示。 下表显示每个可能的阶段及其进度、说明和任何阐明注释。

|  进度 | 说明                                                                                               |  说明 |
|:-----|:--------------------------------------------------------------------------------------------------------------------|:---|
|  0% | 切换处于空闲状态。 |   |
| 2%  | 正在连接源计算机 .。。 |   请确保满足 [源计算机和目标计算机的要求](https://docs.microsoft.com/windows-server/storage/storage-migration-service/overview#security-requirements-the-storage-migration-service-proxy-service-and-firewall-ports) 。|
| 5%  | 正在连接到目标计算机 .。。 |   |
| 6%  | 正在为 Active Directory 中的计算机对象设置安全权限 .。。 |   在目标计算机上复制源计算机的 Active Directory 对象安全权限。|
| 8%  | 确保已成功在源计算机上删除创建的临时帐户 .。。 |   确保可以创建同名的临时帐户。|
| 11% | 正在源计算机上创建临时本地用户帐户 .。。 |   如果源计算机已加入域，则临时帐户用户名为 "MsftSmsStorMigratSvc"。 密码包含127个随机 unicode 宽字符，其中包含字母、数字、符号和大小写更改。 如果源计算机位于工作组中，则使用原始源凭据。|
| 13% | 正在设置源计算机上的本地帐户令牌筛选器策略 .。。 |   禁用该策略，以便我们可以在未加入域时连接到源。 在 [此处](https://support.microsoft.com/help/951016/description-of-user-account-control-and-remote-restrictions-in-windows)了解有关本地帐户令牌筛选器策略的详细信息。|
| 16% | 正在使用临时本地用户帐户连接到源计算机 .。。 |   |
| 19% | 确保在目标计算机上已成功删除我们创建的临时帐户 .。。 |   |
| 22% | 正在目标计算机上创建临时本地用户帐户 .。。 | 如果目标计算机已加入域，则临时帐户用户名为 "MsftSmsStorMigratSvc"。 密码包含127个随机 unicode 宽字符，其中包含字母、数字、符号和大小写更改。 如果目标计算机在工作组中，则使用原始目标凭据。 |
| 25% | 正在设置目标计算机上的本地帐户令牌筛选器策略 .。。 | 禁用该策略，以便我们可以在未加入域时连接到目标。 在 [此处](https://support.microsoft.com/help/951016/description-of-user-account-control-and-remote-restrictions-in-windows)了解有关本地帐户令牌筛选器策略的详细信息。   |
| 27% | 正在使用临时本地用户帐户连接到目标计算机 .。。 |   |
| 30% | 正在从域中删除源计算机 .。。 |   |
| 超过 | 收集源计算机 IP 地址。 |   仅适用于 Linux 源计算机。 |
| 33% | 正在重启源计算机 ... (第一次重启)  |   |
| 36% | 正在等待源计算机在第一次重新启动之后响应 .。。 |   如果源计算机未被 DHCP 子网覆盖，但你在网络配置过程中选择了 DHCP，则可能会变得不响应。|
| 38% | 映射源计算机上的网络接口 .。。 |   |
| 41% | 正在重命名源计算机 .。。 |   |
| 42% | 正在重启源计算机 ... (第一次重启)  |   仅适用于 Linux 源计算机。|
| 43% | 正在重启源计算机 ... (第二次重启)  |   仅适用于已加入域的 Windows Server 2003 源计算机。|
| 43% | 正在等待源计算机在第一次重新启动之后响应 .。。 |   |
| 43% | 在第二次重启后等待源计算机响应 .。。 |   |
| 44% | 正在将源计算机添加到域 .。。 |   |
| 47% | 正在重启源计算机 ... (第一次重启)  |   |
| 50% | 正在重启源计算机 ... (第二次重启)  |   |
| 51% | 正在重启源计算机 ... (第三次重启)  |   仅适用于 Windows Server 2003 源计算机。|
| 52% | 正在等待源计算机响应 .。。 |   |
| 52% | 正在等待源计算机在第一次重新启动之后响应 .。。 |   |
| 55% | 在第二次重启后等待源计算机响应 .。。 |   |
| 56% | 正在等待源计算机响应第三次重启 .。。 |   |
| 57% | 正在删除源上的备用计算机名称 .。。 |   确保源无法与其他用户和应用程序访问。 有关详细信息，请参阅 [Netdom computername](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc835082(v=ws.11))。 |
| 58% | 正在删除在源计算机上创建的临时本地帐户 .。。 |   |
| 61% | 正在重置源计算机上的本地帐户令牌筛选器策略 .。。 |   启用策略。|
| 63% | 正在从域中删除目标计算机 .。。 |   |
| 66% | 正在重启目标计算机 ... (第一次重启)  |   |
| 69% | 正在等待目标计算机在第一次重新启动之后响应 .。。 |   |
| 72% | 映射目标计算机上的网络接口 .。。 |  将源计算机中的每个网络适配器和 IP 地址映射到目标计算机，替换目标的网络信息。   |
| 75% | 正在重命名目标计算机 .。。 |   |
| 77% | 正在将目标计算机添加到域 .。。 |  目标计算机接管旧的源计算机的 Active Directory 对象。 如果目标用户不是 "域管理员" 的成员，或者没有源计算机 Active Directory 对象的管理员权限，则这可能会失败。 在开始转换之前，可以在 "输入凭据" 步骤中指定备用目标凭据。|
| 80% | 正在重启目标计算机 ... (第一次重启)  |   |
| 83% | 正在重启目标计算机 ... (第二次重启)  |   |
| 84% | 正在等待目标计算机响应 .。。 |   |
| 86% | 正在等待目标计算机在第一次重新启动之后响应 .。。 |   |
| 88% | 等待目标计算机在第二次重启后响应 .。。 |   |
| 91% | 正在等待目标计算机响应新名称 .。。 |  由于 Active Directory 和 DNS 复制，可能需要较长时间。 |
| 93% | 正在删除目标上的其他计算机名称 .。。 |   确保已替换目标名称。|
| 94% | 正在删除在目标计算机上创建的临时本地帐户 .。。|   |
| 97% | 正在重置目标计算机上的本地帐户令牌筛选器策略 .。。 |   启用策略。|
|  (100% )  | 成功 |   |

## <a name="faq"></a>常见问题解答

### <a name="__is-domain-controller-migration-supported__"></a>__是否支持域控制器迁移？__

目前不是，但请参阅 [FAQ 页面](https://docs.microsoft.com/windows-server/storage/storage-migration-service/faq#is-domain-controller-migration-supported) 了解解决方法。


## <a name="known-issues"></a>已知问题
>确保已满足 [存储迁移服务概述](overview.md) 中的要求，并在运行存储迁移服务的计算机上安装了最新的 Windows 更新。

有关以下问题的详细信息，请参阅 [已知问题页](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues) 。
* [__存储迁移服务转换验证失败，出现错误 "对目标计算机上的令牌筛选器策略的访问被拒绝"__](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues#storage-migration-service-cutover-validation-fails-with-error-access-is-denied-for-the-token-filter-policy-on-destination-computer)

* [__错误 "针对网络名称资源 CLUSCTL_RESOURCE_NETNAME_REPAIR_VCO 失败"，Windows Server 2008 R2 群集切换失败__](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues#error-clusctl_resource_netname_repair_vco-failed-against-netname-resource-and-windows-server-2008-r2-cluster-cutover-fails)

* [__在源计算机上的 "38% 映射网络接口" 上切换挂起使用静态 Ip 时__](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues#cutover-hangs-on-38-mapping-network-interfaces-on-the-source-computer-when-using-static-ips)

* [__在源计算机上的 "38% 映射网络接口" 上切换挂起__](https://docs.microsoft.com/windows-server/storage/storage-migration-service/known-issues#cutover-hangs-on-38-mapping-network-interfaces-on-the-source-computer)

## <a name="additional-references"></a>其他参考

- [存储迁移服务概述](overview.md)
- [使用存储迁移服务迁移文件服务器](migrate-data.md)
- [存储迁移服务常见问题解答 (FAQ) ](faq.md)
- [存储迁移服务的已知问题](known-issues.md)
