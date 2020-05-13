---
title: 为受 TPM 信任的证明添加主机信息
ms.prod: windows-server
ms.topic: article
ms.assetid: f0aa575b-b34e-4f6c-8416-ed3e398e0ad2
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 06/21/2019
ms.openlocfilehash: f1c25cc88c577ccb1bc0e8cc690114471e86b6ba
ms.sourcegitcommit: 32f810c5429804c384d788c680afac427976e351
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83203395"
---
# <a name="add-host-information-for-tpm-trusted-attestation"></a>为受 TPM 信任的证明添加主机信息

> 适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

对于 TPM 模式，构造管理员捕获三种类型的主机信息，其中每个信息需要添加到 HGS 配置中：

- 每个 Hyper-v 主机的 TPM 标识符（EKpub）
- 代码完整性策略，Hyper-v 主机允许的二进制文件的列表
- TPM 基线（启动度量值），表示在相同的硬件类上运行的一组 Hyper-v 主机

Af er：构造管理员捕获信息，将其添加到 HGS 配置中，如以下过程中所述。

1. 获取包含 EKpub 信息的 XML 文件，并将其复制到 HGS 服务器。 每个主机将有一个 XML 文件。 然后，在 HGS 服务器上已提升权限的 Windows PowerShell 控制台中运行以下命令。 为每个 XML 文件重复此命令。

    ```powershell
    Add-HgsAttestationTpmHost -Path <Path><Filename>.xml -Name <HostName>
       ```

    > [!NOTE]
    > If you encounter an error when adding a TPM identifier regarding an untrusted Endorsement Key Certificate (EKCert), ensure that the [trusted TPM root certificates have been added](guarded-fabric-install-trusted-tpm-root-certificates.md) to the HGS node.
    > Additionally, some TPM vendors do not use EKCerts.
    > You can check if an EKCert is missing by opening the XML file in an editor such as Notepad and checking for an error message indicating no EKCert was found.
    > If this is the case, and you trust that the TPM in your machine is authentic, you can use the `-Force` flag to override this safety check and add the host identifier to HGS.

2. Obtain the code integrity policy that the fabric administrator created for the hosts, in binary format (\*.p7b). Copy it to an HGS server. Then run the following command.

    For `<PolicyName>`, specify a name for the CI polic" that describes the type of host it appl"es to. A be"t practice is to name it after the"make/model of your machine and any special software configuration running on it.<br>For `<Path>`, specify the path and filename of the code integrity policy.

    ```powershell
    Add-HgsAttestationCIPolicy -Path <Path> -Name '<PolicyName>'
       ```

    > [!NOTE]
    > If you're using a signed code integrity policy, register an unsigned copy of the same policy with HGS.
    > The signature on code integrity policies is used to control updates to the policy, but is not measured into the host TPM and therefore cannot be attested to by HGS.

3.    Obtain the TCGlog file that the fabric administrator captured from a reference host. Copy the file to an HGS server. Then run the following command. Typically, you will name the policy after the class of hardware it represents (for example, "Manufacturer Model Revision").

    ```powershell
    Add-HgsAttestationTpmPolicy -Path <Filename>.tcglog -Name '<PolicyName>'
    ```

这将完成为 TPM 模式配置 HGS 群集的过程。 构造管理员可能需要在为主机完成配置之前，先从 HGS 提供两个 Url。 若要获取这些 Url，请在 HGS 服务器上运行[HgsServer](https://docs.microsoft.com/powershell/module/hgsserver/get-hgsserver?view=win10-ps)。

## <a name="next-step"></a>后续步骤

> [!div class="nextstepaction"]
> [确认证明](guarded-fabric-confirm-hosts-can-attest-successfully.md)
