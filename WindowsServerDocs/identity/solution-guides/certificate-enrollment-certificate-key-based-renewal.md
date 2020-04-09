---
title: 为自定义端口上的基于证书密钥的续订配置证书注册 Web 服务
author: Deland-Han
ms.author: delhan
manager: dcscontentpm
ms.date: 11/12/2019
ms.topic: article
ms.prod: windows-server
ms.openlocfilehash: a21a34448248658d2ceffcad07d2a4e6e17b9348
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856340"
---
# <a name="configuring-certificate-enrollment-web-service-for-certificate-key-based-renewal-on-a-custom-port"></a>为自定义端口上的基于证书密钥的续订配置证书注册 Web 服务

> 作者： Jitesh Thakur、Meera Mohideen、包含 Windows 组的技术顾问。
Ankit Tyagi 支持工程师和 Windows 组

## <a name="summary"></a>摘要

本文提供了在443以外的自定义端口上实现证书注册策略 Web 服务（CEP）和证书注册 Web 服务（CES）的分步说明，以利用 CEP 和 CES 的自动续订功能。

本文还介绍了 CEP 和 CES 如何工作，并提供了安装指南。

> [!Note]
> 本文中包含的工作流适用于特定方案。 相同的工作流可能不适用于不同的情况。 但是，原则会保持不变。
>
> 免责声明：此设置是为特定要求创建的，你不想使用端口443来进行 CEP 和 CES 服务器的默认 HTTPS 通信。 虽然这种设置是可能的，但它具有有限的可支持性。 如果遵循本指南，请仔细使用所提供 web 服务器配置的最小偏差，以获得最佳的客户服务和支持。

## <a name="scenario"></a>方案

在此示例中，说明基于使用以下配置的环境：

- 具有 Active Directory 证书服务（AD CS）公钥基础结构（PKI）的 Contoso.com 林。

- 在一个在服务帐户下运行的服务器上配置的两个 CEP/CES 实例。 一个实例使用用户名和密码进行初始注册。 另一种使用基于证书的身份验证在仅续订模式下进行基于密钥的续订。

- 用户具有工作组或未加入域的计算机，他将使用用户名和密码凭据注册计算机证书。

- 从用户到 CEP 的连接和通过 HTTPS 进行的 CES 连接发生在自定义端口上，如49999。 （此端口是从动态端口范围中选择的，并且不会被任何其他服务用作静态端口。）

- 当证书生存期即将结束时，计算机将使用基于证书的 CES 基于密钥的续订来续订同一通道上的证书。

![部署](media/certificate-enrollment-certificate-key-based-renewal-1.png)

## <a name="configuration-instructions"></a>配置说明

### <a name="overview"></a>概述 

1. 为基于密钥的续订配置模板。

2. 作为先决条件，为 "用户名" 和 "密码身份验证" 配置 CEP 和 CES 服务器。   
   在此环境中，将实例称为 "CEPCES01"。

3.  通过在同一服务器上使用 PowerShell 进行基于证书的身份验证来配置其他 CEP 和 CES 实例。 CES 实例将使用服务帐户。

    在此环境中，将实例称为 "CEPCES02"。 所使用的服务帐户为 "cepcessvc"。

4.  配置客户端设置。

### <a name="configuration"></a>配置

本部分提供配置初始注册的步骤。

> [!Note]
> 你还可以配置任何用户服务帐户、MSA 或 GMSA，以供 CES 使用。

作为先决条件，你必须通过使用用户名和密码身份验证在服务器上配置 CEP 和 CES。

#### <a name="configure-the-template-for-key-based-renewal"></a>为基于密钥的续订配置模板

可以复制现有计算机模板，并配置模板的下列设置：

1. 在证书模板的 "使用者名称" 选项卡上，确保选择了 "**在请求中提供**" 和 "**使用现有证书中的使用者信息进行自动注册续订请求**" 选项。
   ![新模板](media/certificate-enrollment-certificate-key-based-renewal-2.png) 

2. 切换到 "**颁发要求**" 选项卡，然后选择 " **CA 证书管理器批准**" 复选框。
   ![颁发要求](media/certificate-enrollment-certificate-key-based-renewal-3.png) 

3. 为此模板将 "**读取**" 和 "**注册**" 权限分配给**cepcessvc**服务帐户。

4. 在 CA 上发布新模板。

> [!Note]
> 请确保模板上的兼容性设置设置为**Windows server 2012 R2** ，因为在兼容性设置为 windows server 2016 或更高版本时，模板不可见的已知问题。 有关信息的详细信息，请参阅[无法从 Windows server 2016 或更高版本的 ca 或 CEP 服务器中选择与 Windows server 2016 CA 兼容的证书模板](https://support.microsoft.com/en-in/help/4508802/cannot-select-certificate-templates-in-windows-server-2016)。


#### <a name="configure-the-cepces01-instance"></a>配置 CEPCES01 实例

##### <a name="step-1-install-the-instance"></a>步骤1：安装实例

若要安装 CEPCES01 实例，请使用以下方法之一。

**方法1**

请参阅以下文章，了解有关为用户名和密码身份验证启用 CEP 和 CES 的分步指导：

[证书注册策略 Web 服务指南](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831625(v=ws.11))

[证书注册 Web 服务指南](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831822(v=ws.11)#configure-a-ca-for-the-certificate-enrollment-web-service)

> [!Note]
> 如果同时配置了 "用户名" 和 "密码身份验证" 的 CEP 和 CES 实例，请确保未选择 "启用基于密钥的续订" 选项。

**方法2**

你可以使用以下 PowerShell cmdlet 来安装 CEP 和 CES 实例：

```PowerShell
Import-Module ServerManager
Add-WindowsFeature Adcs-Enroll-Web-Pol
Add-WindowsFeature Adcs-Enroll-Web-Svc
```

```PowerShell
Install-AdcsEnrollmentPolicyWebService -AuthenticationType Username -SSLCertThumbprint "sslCertThumbPrint"
```

此命令通过指定使用用户名和密码进行身份验证来安装证书注册策略 Web 服务（CEP）。 

> [!Note]
> 在此命令中，\<**SSLCertThumbPrint**\> 是将用于绑定 IIS 的证书的指纹。

```PowerShell
Install-AdcsEnrollmentWebService -ApplicationPoolIdentity -CAConfig "CA1.contoso.com\contoso-CA1-CA" -SSLCertThumbprint "sslCertThumbPrint" -AuthenticationType Username
```

此命令安装证书注册 Web 服务（CES），以将证书颁发机构用于计算机名称**CA1.contoso.com**和**CA1-ca**的 ca 公用名。 已将 CES 标识指定为默认应用程序池标识。 身份验证类型为**username**。 SSLCertThumbPrint 是将用于绑定 IIS 的证书的指纹。

##### <a name="step-2-check-the-internet-information-services-iis-manager-console"></a>步骤2检查 Internet Information Services （IIS）管理器控制台

成功安装后，你希望在 Internet Information Services （IIS）管理器控制台中看到以下显示。
![IIS 管理器](media/certificate-enrollment-certificate-key-based-renewal-4.png) 

在 "**默认**网站" 下，选择 " **ADPolicyProvider_CEP_UsernamePassword**"，然后打开 "**应用程序设置**"。 请注意**ID**和**URI**。

您可以为管理添加**友好名称**。

#### <a name="configure-the-cepces02-instance"></a>配置 CEPCES02 实例

##### <a name="step-1-install-the-cep-and-ces-for-key-based-renewal-on-the-same-server"></a>步骤1：在同一服务器上安装 CEP 和 CES 以实现基于密钥的续订。 

在 PowerShell 中运行以下命令：

```PowerShell
Install-AdcsEnrollmentPolicyWebService -AuthenticationType Certificate -SSLCertThumbprint "sslCertThumbPrint" -KeyBasedRenewal
```

此命令安装证书注册策略 Web 服务（CEP），并指定证书用于身份验证。 

> [!Note]
> 在此命令中，\<SSLCertThumbPrint\> 是将用于绑定 IIS 的证书的指纹。 

基于密钥的续订允许证书客户端使用其现有证书的密钥来续订其证书，以便进行身份验证。 在基于密钥的续订模式下，服务将仅返回为基于密钥的续订设置的证书模板。

```PowerShell
Install-AdcsEnrollmentWebService -CAConfig "CA1.contoso.com\contoso-CA1-CA" -SSLCertThumbprint "sslCertThumbPrint" -AuthenticationType Certificate -ServiceAccountName "Contoso\cepcessvc" -ServiceAccountPassword (read-host "Set user password" -assecurestring) -RenewalOnly -AllowKeyBasedRenewal
```

此命令安装证书注册 Web 服务（CES），以将证书颁发机构用于计算机名称**CA1.contoso.com**和**CA1-ca**的 ca 公用名。 

在此命令中，将证书注册 Web 服务的标识指定为**cepcessvc**服务帐户。 身份验证类型为**certificate**。 **SSLCertThumbPrint**是将用于绑定 IIS 的证书的指纹。

**RenewalOnly** CMDLET 允许 CES 在仅续订模式下运行。 **AllowKeyBasedRenewal** cmdlet 还指定 CES 将接受注册服务器的基于密钥的续订请求。 这些是用于身份验证的有效客户端证书，不直接映射到安全主体。

> [!Note]
> 服务帐户必须是服务器上的**IISUsers**组的一部分。

##### <a name="step-2-check-the-iis-manager-console"></a>步骤2检查 IIS 管理器控制台

成功安装后，你希望在 IIS 管理器控制台中看到以下显示。
![IIS 管理器](media/certificate-enrollment-certificate-key-based-renewal-5.png) 

选择 "**默认**网站" 下的**KeyBasedRenewal_ADPolicyProvider_CEP_Certificate** ，并打开**应用程序设置**。 记下**ID**和**URI**。 您可以为管理添加**友好名称**。

> [!Note]
> 如果实例安装在新服务器上，请仔细检查该 ID，确保该 ID 与在 CEPCES01 实例中生成的 ID 相同。 如果值不相同，则可以直接复制并粘贴值。

#### <a name="complete-certificate-enrollment-web-services-configuration"></a>完成证书注册 Web 服务配置

为了能够代表 CEP 和 CES 的功能注册证书，您必须在 Active Directory 中配置工作组的计算机帐户，然后在服务帐户上配置约束委派。

##### <a name="step-1-create-a-computer-account-of-the-workgroup-computer-in-active-directory"></a>步骤1：在 Active Directory 中创建工作组计算机的计算机帐户

此帐户将用于基于密钥的续订和证书模板上的 "发布到 Active Directory" 选项进行身份验证。

> [!Note]
> 无需加入客户端计算机。 在 KBR for dsmapper service 中进行基于证书的身份验证时，此帐户将进入图片。

![新建对象](media/certificate-enrollment-certificate-key-based-renewal-6.png) 
 
##### <a name="step-2-configure-the-service-account-for-constrained-delegation-s4u2self"></a>步骤2：为约束委派配置服务帐户（S4U2Self）

运行以下 PowerShell 命令以启用约束委托（S4U2Self 或任何身份验证协议）：

```PowerShell
Get-ADUser -Identity cepcessvc | Set-ADAccountControl -TrustedToAuthForDelegation $True
Set-ADUser -Identity cepcessvc -Add @{'msDS-AllowedToDelegateTo'=@('HOST/CA1.contoso.com','RPCSS/CA1.contoso.com')}
```

> [!Note]
> 在此命令中，\<cepcessvc\> 是服务帐户，< CA1 > 是证书颁发机构。

> [!Important]
> 我们未在此配置中启用 CA 上的 RENEWALONBEHALOF 标志，因为我们使用约束委派为我们执行同一作业。 这样，我们便可以避免向 CA 的安全性添加服务帐户的权限。

##### <a name="step-3-configure-a-custom-port-on-the-iis-web-server"></a>步骤3：在 IIS web 服务器上配置自定义端口

1. 在 IIS 管理器控制台中，选择 "默认网站"。

2. 在 "操作" 窗格中，选择 "编辑网站绑定"。 

3. 将默认端口设置从443更改为自定义端口。 示例屏幕快照显示了49999的端口设置。
   ![更改端口](media/certificate-enrollment-certificate-key-based-renewal-7.png) 

##### <a name="step-4-edit-the-ca-enrollment-services-object-on-active-directory"></a>步骤4：在 Active Directory 上编辑 CA 注册服务对象

1. 在域控制器上，打开 "adsiedit"。

2. [连接到配置分区](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/ff730188(v=ws.10))，并导航到 CA 注册服务对象：
   
   CN = ENTCA，CN = 注册服务，CN = Public Key Services，CN = Services，CN = Configuration，DC = contoso，DC = com

3. 右键单击并编辑 CA 对象。 通过将自定义端口与在应用程序设置中找到的 CEP 和 CES 服务器 Uri 结合使用来更改**mspki-site-name**属性。 例如：

   ```
   140https://cepces.contoso.com:49999/ENTCA_CES_UsernamePassword/service.svc/CES0   
   181https://cepces.contoso.com:49999/ENTCA_CES_Certificate/service.svc/CES1
   ```
   
   ![ADSI 编辑](media/certificate-enrollment-certificate-key-based-renewal-8.png) 

#### <a name="configure-the-client-computer"></a>配置客户端计算机

在客户端计算机上，设置注册策略和自动注册策略。 要实现这一点，请执行下列操作：

1. 选择 "**开始** > " "**运行**"，然后输入**gpedit.msc**。

2.  > **安全设置**"中转到"**计算机配置**" > **Windows 设置**"，然后单击 "**公钥策略**"。

3. 启用**证书服务客户端-自动注册策略**以匹配以下屏幕截图中的设置。
   ![证书组策略](media/certificate-enrollment-certificate-key-based-renewal-9.png)
 
4. 启用**证书服务客户端-证书注册策略**。

   a. 单击 "**添加**" 以添加注册策略，并输入在 ADSI 中编辑的**USERNAMEPASSWORD**的 CEP URI。
   
   b. 对于 "**身份验证类型**"，请选择 "**用户名/密码**"。
   
   c. 将优先级设置为**10**，然后验证策略服务器。
      ![注册策略](media/certificate-enrollment-certificate-key-based-renewal-10.png)

   > [!Note]
   > 请确保将端口号添加到 URI，并允许在防火墙上使用。

5. 通过 certlm.msc 为计算机注册第一个证书。
   ![注册策略](media/certificate-enrollment-certificate-key-based-renewal-11.png)

   选择 KBR 模板并注册证书。
   ![注册策略](media/certificate-enrollment-certificate-key-based-renewal-12.png)

6. 重新打开**gpedit.msc** 。 编辑 "**证书服务客户端-证书注册策略**"，然后添加基于密钥的续订注册策略：

   a. 单击 "**添加**"，输入在 ADSI 中编辑的**证书**的 CEP URI。 
   
   b. 将优先级设置为**1**，然后验证策略服务器。 系统将提示你进行身份验证并选择我们最初注册的证书。

   ![注册策略](media/certificate-enrollment-certificate-key-based-renewal-13.png) 

> [!Note]
> 请确保基于密钥的续订注册策略的优先级值低于用户名密码注册策略优先级的优先级值。 第一个首选项的优先级最低。

## <a name="testing-the-setup"></a>测试安装程序

若要确保自动续订正在运行，请通过使用 mmc 续订具有相同密钥的证书来验证手动续订是否正常工作。 此外，在续订时，还应提示您选择证书。 你可以选择前面注册的证书。 应为提示。

打开计算机的 "个人" 证书存储区，然后添加 "存档的证书" 视图。 为此，请将 "本地计算机帐户" 管理单元添加到 mmc.exe，单击 "**证书（本地计算机）"，单击 "证书（本地计算机）** " **，单击右侧**或 mmc 顶部的 "**操作" 选项卡**，单击 "**查看选项**"，选择 "**存档的证书**"，然后单击 **"确定"** 。

### <a name="method-1"></a>方法 1 

运行以下命令：

```PowerShell
certreq -machine -q -enroll -cert <thumbprint> renew
```

![命令](media/certificate-enrollment-certificate-key-based-renewal-14.png)

### <a name="method-2"></a>Method 2

将客户端计算机上的时间和日期提前到证书模板的续订时间。

例如，证书模板具有2天的有效性设置和配置的8小时续订设置。 在凌晨4:00 颁发了示例证书。 每月18日过期，截止时间为凌晨4:00。 20号。 自动注册引擎会在重新启动时触发，每隔8小时触发一次（大约）。

因此，如果您将时间前进到 8:10 P.M.。 在19年，由于我们的续订窗口在模板上设置为8小时，因此运行 Certutil-脉冲（触发 AE 引擎）可为您注册证书。

![命令](media/certificate-enrollment-certificate-key-based-renewal-15.png)
 
测试完成后，将时间设置恢复为原始值，然后重新启动客户端计算机。

> [!Note]
> 前面的屏幕截图是演示自动注册引擎按预期工作的示例，因为 CA 日期仍设置为18。 因此，它会继续颁发证书。 在实际情况下，将不会进行大量的续订。

## <a name="references"></a>参考

[测试实验室指南：演示基于证书密钥的续订](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj590165(v%3Dws.11))

[证书注册 Web 服务](https://techcommunity.microsoft.com/t5/Ask-the-Directory-Services-Team/Certificate-Enrollment-Web-Services/ba-p/397385)

[安装-AdcsEnrollmentPolicyWebService](https://docs.microsoft.com/powershell/module/adcsdeployment/install-adcsenrollmentpolicywebservice?view=win10-ps)

[安装-AdcsEnrollmentWebService](https://docs.microsoft.com/powershell/module/adcsdeployment/install-adcsenrollmentwebservice?view=win10-ps)

另请参阅

[Windows Server 安全论坛](https://aka.ms/adcsforum)

[Active Directory 证书服务（AD CS）公钥基础结构（PKI）常见问题（FAQ）](https://aka.ms/adcsfaq)

[Windows PKI 文档参考和库](https://social.technet.microsoft.com/wiki/contents/articles/987.windows-pki-documentation-reference-and-library.aspx)

[Windows PKI 博客](https://blogs.technet.com/b/pki/)

[如何在 Web 注册代理页的自定义服务帐户上配置 Kerberos 约束委派（仅限 S4U2Proxy 或 Kerberos）](https://support.microsoft.com/help/4494313/configuring-web-enrollment-proxy-for-s4u2proxy-constrained-delegation)