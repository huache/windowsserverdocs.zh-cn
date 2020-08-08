---
title: 管理传输层安全性 (TLS)
description: Windows Server 安全
ms.topic: article
author: justinha
ms.author: justinha
manager: brianlic
ms.date: 05/16/2018
ms.openlocfilehash: 30ab0547fd538eec3f50120a5d536eb9a48de54b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971284"
---
# <a name="manage-transport-layer-security-tls"></a>管理传输层安全性 (TLS)

> 适用于： Windows Server (半年通道) ，Windows Server 2016，Windows 10

## <a name="configuring-tls-cipher-suite-order"></a>配置 TLS 密码套件顺序

不同的 Windows 版本支持不同的 TLS 密码套件和优先级顺序。 请参阅[TLS/SSL 中的密码套件 (SCHANNEL SSP) ](https://docs.microsoft.com/windows/win32/secauthn/cipher-suites-in-schannel) ，以获得不同 Windows 版本中 Microsoft Schannel 提供程序支持的默认顺序。

> [!NOTE]
> 还可以通过使用 CNG 函数修改密码套件的列表，有关详细信息，请参阅[优先级 Schannel 密码套件](https://docs.microsoft.com/windows/win32/secauthn/prioritizing-schannel-cipher-suites)。

更改 TLS 密码套件顺序将在下一次启动时生效。 在重启或关闭之前，现有顺序将有效。

> [!WARNING]
> 不支持为默认优先级排序更新注册表设置，可以通过服务更新进行重置。

### <a name="configuring-tls-cipher-suite-order-by-using-group-policy"></a>使用组策略配置 TLS 密码套件顺序

你可以使用 SSL 密码套件顺序组策略设置来配置默认的 TLS 密码套件顺序。

1. 在组策略管理控制台中， **Computer Configuration**  >  **管理模板**  >  **网络**  >  **SSL 配置设置**"中转到" 计算机配置 "。
2. 双击 " **SSL 密码套件顺序**"，然后单击 "**已启用**" 选项。
3. 右键单击 " **SSL 密码套件**" 框，然后从弹出菜单中选择 "全**选**"。

   ![组策略设置](../media/Transport-Layer-Security-protocol/ssl-cipher-suite-order-gp-setting.png)

4. 右键单击所选文本，然后从弹出菜单中选择 "**复制**"。
5. 将文本粘贴到文本编辑器（如 notepad.exe），并使用新的密码套件顺序列表进行更新。

   > [!NOTE]
   > TLS 密码套件顺序列表必须采用严格的逗号分隔格式。 每个密码套件字符串都以逗号 ( 结尾，) 到右侧。
   >
   > 此外，密码套件的列表限制为1023个字符。

6. 将**SSL 密码套件**中的列表替换为更新的排序列表。
7. 单击“**确定**”或“**应用**”。

### <a name="configuring-tls-cipher-suite-order-by-using-mdm"></a>使用 MDM 配置 TLS 密码套件顺序

Windows 10 策略 CSP 支持 TLS 密码套件的配置。 有关详细信息，请参阅[加密/TLSCipherSuites](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-tlsciphersuites) 。

### <a name="configuring-tls-cipher-suite-order-by-using-tls-powershell-cmdlets"></a>使用 TLS PowerShell Cmdlet 配置 TLS 密码套件顺序

TLS PowerShell 模块支持获取 TLS 密码套件、禁用密码套件和启用密码套件的排序列表。 有关详细信息，请参阅[TLS 模块](https://docs.microsoft.com/powershell/module/tls/?view=win10-ps)。

## <a name="configuring-tls-ecc-curve-order"></a>配置 TLS ECC 曲线顺序

从 Windows 10 开始 & Windows Server 2016，可以独立于密码套件顺序配置 ECC 曲线顺序。 如果 TLS 密码套件顺序列表具有椭圆曲线后缀，则在启用时，它们将被新的椭圆曲线优先级顺序替代。 这允许组织使用组策略对象来配置具有相同密码套件顺序的不同 Windows 版本。

> [!NOTE]
> 在 Windows 10 之前，密码套件后面追加了椭圆曲线来确定曲线优先级。

### <a name="managing-windows-ecc-curves-using-certutil"></a>使用 CertUtil 管理 Windows ECC 曲线

从 Windows 10 和 Windows Server 2016 开始，Windows 通过命令行实用工具 certutil.exe 提供椭圆曲线参数管理。
椭圆曲线参数存储在 bcryptprimitives.dll 中。 使用 certutil.exe，管理员可分别在 Windows 中添加和删除曲线参数。 Certutil.exe 将曲线参数安全地存储在注册表中。
Windows 可以通过与曲线关联的名称开始使用曲线参数。

#### <a name="displaying-registered-curves"></a>显示已注册曲线

使用以下 certutil.exe 命令显示为当前计算机注册的曲线列表。

```powershell
certutil.exe –displayEccCurve
```

![Certutil 显示曲线](../media/Transport-Layer-Security-protocol/certutil-display-curves.png)

*图 1 Certutil.exe 输出显示已注册曲线的列表。*

#### <a name="adding-a-new-curve"></a>添加新曲线

组织可以创建和使用其他受信任实体所研究的曲线参数。
希望在 Windows 中使用这些新曲线的管理员必须添加曲线。
使用以下 certutil.exe 命令将曲线添加到当前计算机：

```powershell
Certutil —addEccCurue curveName curveParameters [curveOID] [curveType]
```

- **CurveName**参数表示添加了曲线参数的曲线的名称。
- **CurveParameters**参数表示包含要添加的曲线参数的证书的文件名。
- **CurveOid**参数表示包含要添加 (可选) 的曲线参数的 OID 的证书的文件名。
- **CurveType**参数表示[EC 命名曲线注册表](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8)中命名曲线的十进制值 (可选) 。

![Certutil 添加曲线](../media/Transport-Layer-Security-protocol/certutil-add-curves.png)

*图2使用 certutil.exe 添加曲线。*

#### <a name="removing-a-previously-added-curve"></a>移除以前添加的曲线

管理员可以使用以下 certutil.exe 命令删除先前添加的曲线：

```powershell
Certutil.exe –deleteEccCurve curveName
```

在管理员从计算机中删除曲线后，Windows 无法使用已命名的曲线。

## <a name="managing-windows-ecc-curves-using-group-policy"></a>使用组策略管理 Windows ECC 曲线

组织可以使用组策略和组策略首选项注册表扩展将曲线参数分配给企业、已加入域的计算机。
分布曲线的过程如下：

1. 在 Windows 10 和 Windows Server 2016 上，使用**certutil.exe**将新的已注册命名曲线添加到 windows。
2. 在同一台计算机上，打开组策略管理控制台 (GPMC) ，创建新的组策略对象，并对其进行编辑。
3. 导航到 "**计算机配置" |首选项 |Windows 设置 |注册表**。  右键单击 "**注册表**"。 悬停在 "**新建**" 上并选择 "**收集项**"。 重命名收集项以匹配曲线的名称。 将为*HKEY_LOCAL_MACHINE \currentcontrolset\control\cryptography\eccparameters*下的每个注册表项创建一个注册表项。
4. 通过为*HKEY_LOCAL_MACHINE \Currentcontrolset\control\cryptography\eccparameters \[ curveName]* 下列出的每个注册表值添加新的**注册表项**，来配置新创建的组策略首选项注册表集合。
5. 将包含组策略注册表收集项的组策略对象部署到应接收新命名曲线的 Windows 10 和 Windows Server 2016 计算机。

    ![GPP 分布曲线](../media/Transport-Layer-Security-protocol/gpp-distribute-curves.png)

    *图3使用组策略首选项来分布曲线*

## <a name="managing-tls-ecc-order"></a>管理 TLS ECC 顺序

从 Windows 10 和 Windows Server 2016 开始，可以使用 ECC 曲线顺序组策略设置来配置默认 TLS ECC 曲线顺序。
使用通用 ECC 和此设置，组织可以将其自己的受信任的命名曲线 (，它们已批准与 TLS) 用于操作系统，然后将这些命名曲线添加到曲线优先级组策略设置，以确保在未来的 TLS 握手中使用它们。
接收策略设置后，下一次重新启动时，新的曲线优先级列表将变为活动状态。

![GPP 分布曲线](../media/Transport-Layer-Security-protocol/gp-managing-tls-curve-priority-order.png)

*图4使用组策略管理 TLS 曲线优先级*

