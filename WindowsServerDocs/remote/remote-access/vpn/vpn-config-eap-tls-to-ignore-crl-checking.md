---
title: 配置 EAP-TLS 以忽略证书吊销列表 (CRL) 检查
description: 如果 NPS 服务器已完成证书 (链的吊销检查（包括客户端的根证书) ）并验证证书已被吊销，则 EAP-TLS 客户端将无法连接。
ms.topic: article
ms.date: 07/13/2018
ms.author: v-tea
author: Teresa-MOTIV
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: 6ef6294863807b20558264a5b02069a64499ae55
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87958125"
---
# <a name="step-71-configure-eap-tls-to-ignore-certificate-revocation-list-crl-checking"></a>步骤 7.1： 配置 EAP-TLS 以忽略证书吊销列表 (CRL) 检查

>适用于： Windows Server (半年通道) ，Windows Server 2016，Windows Server 2012 R2，Windows 10

- [**上一个：** 步骤7。使用 Azure AD (可选) VPN 连接的条件性访问](ad-ca-vpn-connectivity-windows10.md)
- [**下一步：** 步骤7.2。创建用于 VPN 身份验证的根证书 Azure AD](vpn-create-root-cert-for-vpn-auth-azure-ad.md)

>[!IMPORTANT]
>未能实现此注册表更改将导致使用 cloud 证书和 PEAP 的 IKEv2 连接失败，但使用从本地 CA 颁发的客户端身份验证证书的 IKEv2 连接将继续工作。

在此步骤中，你可以添加**IgnoreNoRevocationCheck** ，并将其设置为在证书不包括 CRL 分发点时允许客户端进行身份验证。 默认情况下，IgnoreNoRevocationCheck 设置为 0 (禁用) 。

>[!NOTE]
>如果 Windows 路由和远程访问服务器 (RRAS) 使用 NPS 将 RADIUS 调用代理到另一个 NPS，则必须在两个服务器上设置**IgnoreNoRevocationCheck = 1** 。

除非 NPS 服务器完成证书链的吊销检查（包括根证书)  (），否则 EAP-TLS 客户端无法连接。 Azure AD 颁发给用户的云证书没有 CRL，因为它们是生存期为一小时的短有效期证书。 需要将 NPS 上的 EAP 配置为忽略缺少 CRL 的情况。 默认情况下，IgnoreNoRevocationCheck 设置为 0 (禁用) 。 添加 IgnoreNoRevocationCheck 并将其设置为1，以允许当证书不包括 CRL 分发点时对客户端进行身份验证。

因为身份验证方法是 EAP-TLS，所以仅在 EAP\13. 下需要此注册表值。 如果使用其他 EAP 身份验证方法，则还应将注册表值添加到这些方法下。

**方法**

1. 在 NPS 服务器上打开**regedit.exe** 。

2. 导航到**HKEY_LOCAL_MACHINE \system\currentcontrolset\services\rasman\ppp\eap\13**"。

3. 选择 "**编辑 >** " "新建"，并选择 " **DWORD (32 位) 值**并输入**IgnoreNoRevocationCheck**。

4. 双击 " **IgnoreNoRevocationCheck** "，并将 "值" 数据设置为**1**。

5. 选择 **"确定"** ，然后重新启动服务器。 重新启动 RRAS 和 NPS 服务无法满足要求。

有关详细信息，请参阅[如何启用或禁用证书吊销检查 (CRL) 在客户端上](/previous-versions/system-center/configuration-manager-2007/bb680540(v=technet.10))。


|注册表路径  |EAP 扩展  |
|---------|---------|
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\13     |EAP-TLS         |
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\25     |PEAP         |
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\26     |MSCHAP v2         |

## <a name="next-steps"></a>后续步骤

[步骤7.2。使用 Azure AD 创建用于 VPN 身份验证的根证书](vpn-create-root-cert-for-vpn-auth-azure-ad.md)：在此步骤中，你将使用 Azure AD 配置用于 vpn 身份验证的条件性访问根证书，该证书将在租户中自动创建 Vpn 服务器云应用。
