---
title: 确认受保护的主机可以证明
ms.prod: windows-server
ms.topic: article
ms.assetid: 7485796b-b840-4678-9b33-89e9710fbbc7
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 09/25/2019
ms.openlocfilehash: aa2075bda71c6713fa76577b685315118199e63b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856780"
---
# <a name="confirm-guarded-hosts-can-attest"></a>确认受保护的主机可以证明

>适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

构造管理员需要确认 Hyper-v 主机是否可以作为受保护的主机运行。 在至少一个受保护的主机上完成以下步骤：

1. 如果尚未安装 Hyper-v 角色和主机保护者 Hyper-v 支持功能，请使用以下命令安装它们：

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ```

2. 请确保 Hyper-v 主机可以解析 HGS DNS 名称，并且可以通过网络连接来访问 HGS 服务器上的端口80（或者，如果设置了 HTTPS，则为443）。

3. 配置主机的密钥保护和证明 Url：

    - **通过 Windows powershell**：你可以通过在提升的 Windows powershell 控制台中执行以下命令来配置密钥保护和证明 url。 对于 &lt;FQDN&gt;，请使用 HGS 群集的完全限定的域名（FQDN）（例如，HgsServer），或要求 HGS 管理员在 HGS 服务器上运行**Get-HgsServer** cmdlet 以检索 url。

        ```PowerShell
        Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'
         ```

        若要配置回退 HGS 服务器，请重复此命令并指定密钥保护和证明服务的备用 Url。 有关详细信息，请参阅[回退配置](guarded-fabric-manage-branch-office.md#fallback-configuration)。

    - **通过 vmm**：如果你使用的是 System Center 2016-VIRTUAL MACHINE MANAGER （VMM），则可在 VMM 中配置证明和密钥保护 url。 有关详细信息，请参阅在**VMM 中设置受保护的主机**中[配置全局 HGS 设置](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts#configure-global-hgs-settings)。

    >**注意**
    > - 如果 HGS 管理员在[hgs 服务器上启用了 HTTPS](guarded-fabric-configure-hgs-https.md)，则以 `https://`开始 url。
    > - 如果 HGS 管理员在 HGS 服务器上启用了 HTTPS，并使用了自签名证书，则需要将证书导入到每个主机上受信任的根证书颁发机构存储区中。 为此，请在每个主机上运行以下命令：
       ```PowerShell
       Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root
       ```
    > - 如果已将 HGS 客户端配置为使用 HTTPS 并禁用了系统范围内的 TLS 1.0，请参阅我们的[新式 tls 指南](guarded-fabric-troubleshoot-hosts.md#modern-tls)

4. 若要在主机上启动证明尝试并查看证明状态，请运行以下命令：

    ```powershell
    Get-HgsClientConfiguration
    ```

    该命令的输出指示主机是否已通过证明，现已受到保护。 如果 `IsHostGuarded` 未返回**True**，则可以运行 HGS 诊断工具[HgsTrace](https://technet.microsoft.com/library/mt718831.aspx)，以进行调查。 若要运行诊断，请在主机上权限提升的 Windows PowerShell 提示符下输入以下命令：

    ```powershell
    Get-HgsTrace -RunDiagnostics -Detailed
    ```

    > [!IMPORTANT]
    > 如果使用的是 Windows Server 2019 或 Windows 10 1809 版，并且使用的是代码完整性策略，`Get-HgsTrace` 将为**代码完整性策略活动**诊断返回失败。
    > 如果这是唯一失败的诊断，则可以安全地忽略此结果。

## <a name="next-step"></a>下一步

> [!div class="nextstepaction"]
> [部署受防护的 VM](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

## <a name="see-also"></a>另请参阅

- [部署主机保护者服务（HGS）](guarded-fabric-deploying-hgs-overview.md)
- [部署受防护的 VM](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
