---
title: 在新的专用林中使用 AD 模式初始化 HGS 群集（默认值）
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 851ee57545aa233fd7d6c728b213ba687a1c1371
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856680"
---
# <a name="initialize-the-hgs-cluster-using-ad-mode-in-a-new-dedicated-forest-default"></a>在新的专用林中使用 AD 模式初始化 HGS 群集（默认值）

>适用于：Windows Server（半年频道）、Windows Server 2016

>[!IMPORTANT]
>从 Windows Server 2019 开始，已弃用管理受信任的证明（AD 模式）。 对于不可能进行 TPM 证明的环境，请配置[主机密钥证明](guarded-fabric-initialize-hgs-key-mode-default.md)。 主机密钥证明向 AD 模式提供类似的保障，并更易于设置。 

1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)] 
2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  在已提升权限的 PowerShell 窗口中，在第一个 HGS 节点上运行[HgsServer](https://technet.microsoft.com/library/mt652185.aspx) 。 此 cmdlet 的语法支持多种不同的输入，但最常见的两个调用如下：

    -   如果使用 PFX 文件进行签名和加密证书，请运行以下命令：

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustActiveDirectory
        ```

    -   如果你使用的是本地证书存储中安装的不可导出的证书，请运行以下命令。 如果你不知道证书的指纹，可以通过运行 `Get-ChildItem Cert:\LocalMachine\My`列出可用的证书。

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' --TrustActiveDirectory
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]  

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]

## <a name="next-step"></a>下一步

> [!div class="nextstepaction"]
> [配置结构 DNS](guarded-fabric-configuring-fabric-dns-ad.md)