---
title: '使用新的专用林中的密钥模式初始化 HGS 群集 (默认值) '
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 9098c339207464df3bf2eefa0e18250d2356a072
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950902"
---
# <a name="initialize-the-hgs-cluster-using-key-mode-in-a-new-dedicated-forest-default"></a>使用新的专用林中的密钥模式初始化 HGS 群集 (默认值) 

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016


1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)]
2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  在已提升权限的 PowerShell 窗口中，在第一个 HGS 节点上运行[HgsServer](https://technet.microsoft.com/library/mt652185.aspx) 。 此 cmdlet 的语法支持多种不同的输入，但最常见的两个调用如下：

    -   如果使用 PFX 文件进行签名和加密证书，请运行以下命令：

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustHostkey
        ```

    -   如果你使用的是本地证书存储中安装的不可导出的证书，请运行以下命令。 如果你不知道证书的指纹，可以通过运行来列出可用的证书 `Get-ChildItem Cert:\LocalMachine\My` 。

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' --TrustHostKey
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]


## <a name="next-step"></a>后续步骤

> [!div class="nextstepaction"]
> [创建主机密钥](guarded-fabric-create-host-key.md)