---
ms.assetid: 102eeeb1-6c55-42a2-b321-71a7dab46146
title: AD FS Windows Server 2016 中的访问控制策略
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 7ed0360c9fcbdabab7ae731b8816049b58765f2b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87947357"
---
# <a name="access-control-policies-in-windows-server-2016-ad-fs"></a>Windows Server 2016 AD FS 中的访问控制策略


## <a name="access-control-policy-templates-in-ad-fs"></a>AD FS 中的访问控制策略模板
Active Directory 联合身份验证服务现在支持使用访问控制策略模板。  通过使用访问控制策略模板，管理员可以通过将策略模板分配给一组依赖方 (RPs) 来强制执行策略设置。 管理员还可以对策略模板进行更新，如果不需要用户交互，则会自动将更改应用到信赖方。

## <a name="what-are-access-control-policy-templates"></a>什么是访问控制策略模板？
用于策略处理 AD FS 核心管道分为三个阶段：身份验证、授权和声明颁发。 目前，AD FS 管理员必须分别为这些阶段中的每个阶段配置策略。  这还涉及了解这些策略的含义，以及这些策略是否具有依赖关系。 此外，管理员必须了解声明规则语言并创作自定义规则，以启用一些简单/常见策略 (例如。 阻止外部访问) 。

访问控制策略模板的作用是替换此旧模型，管理员必须使用声明语言配置颁发授权规则。  颁发授权规则的旧 PowerShell cmdlet 仍适用，但它与新模型互斥。 管理员可以选择使用新模型或旧模型。  新模型允许管理员控制何时授予访问权限，包括强制执行多重身份验证。

访问控制策略模板使用允许模型。  这意味着，默认情况下，任何人都无法访问，并且必须显式授予访问权限。  但是，这并不只是全部或全部都允许。  管理员可以向允许规则添加例外。  例如，管理员可能希望基于特定网络授予访问权限，方法是选择此选项并指定 IP 地址范围。  但管理员可以添加和例外，例如，管理员可能会从特定网络添加例外，并指定该 IP 地址范围。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP2.PNG)

## <a name="built-in-access-control-policy-templates-vs-custom-access-control-policy-templates"></a>内置的访问控制策略模板与自定义访问控制策略模板
AD FS 包括几个内置的访问控制策略模板。  这些是指具有相同策略要求集的一些常见方案，例如，适用于 Office 365 的客户端访问策略。  不能修改这些模板。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP3.PNG)

为了提供更高的灵活性以满足你的业务需求，管理员可以创建自己的访问策略模板。  这些可以在创建后进行修改，对自定义策略模板的更改将应用到由这些策略模板控制的所有 RPs。  若要添加自定义策略模板，只需在 "AD FS 管理" 中单击 "添加访问控制策略"。

若要创建策略模板，管理员需要首先指定将授权请求用于令牌颁发和/或委派的条件。 条件和操作选项显示在下表中。   具有不同值或新值的管理员可以进一步配置粗体条件。 管理员还可以指定异常（如果有）。 满足条件时，如果指定了异常并且传入请求与异常中指定的条件匹配，则不会触发允许操作。

|允许用户|Except|
| --- | --- |
 |从**特定**网络|从**特定**网络<p>从**特定**组<p>从具有**特定**信任级别的设备<p>具有请求中的**特定**声明|
|从**特定**组|从**特定**网络<p>从**特定**组<p>从具有**特定**信任级别的设备<p>具有请求中的**特定**声明|
|从具有**特定**信任级别的设备|从**特定**网络<p>从**特定**组<p>从具有**特定**信任级别的设备<p>具有请求中的**特定**声明|
|具有请求中的**特定**声明|从**特定**网络<p>从**特定**组<p>从具有**特定**信任级别的设备<p>具有请求中的**特定**声明|
|和需要多重身份验证|从**特定**网络<p>从**特定**组<p>从具有**特定**信任级别的设备<p>具有请求中的**特定**声明|

如果管理员选择了多个条件，则它们是**和**关系。 操作是互相排斥的，对于一个策略规则，只能选择一个操作。 如果管理员选择了多个异常，则它们是**或**关系。 下面显示了几个策略规则示例：

|**策略**|**策略规则**|
| --- | --- |
|Extranet 访问需要 MFA<p>允许所有用户|**规则 #1**<p>从**extranet**<p>具有 MFA 的和<p>允许<p>**规则 # 2**<p>从**intranet**<p>允许|
|除非 FTE 外，不允许外部访问<p>允许对已加入工作区的设备上的 FTE 进行 Intranet 访问|**规则 #1**<p>从**extranet**<p>和**非 FTE**组<p>允许<p>**规则 #2**<p>从**intranet**<p>以及从已**加入工作区**的设备<p>和来自**FTE**组<p>允许|
|Extranet 访问需要 MFA，但 "服务管理员" 除外<p>允许所有用户访问|**规则 #1**<p>从**extranet**<p>具有 MFA 的和<p>允许<p>**服务管理员组**除外<p>**规则 #2**<p>通用<p>允许|
|从 extranet 访问的非工作位置加入设备需要 MFA<p>允许 AD fabric 进行 intranet 和 extranet 访问|**规则 #1**<p>从**intranet**<p>和从**AD Fabric**组<p>允许<p>**规则 #2**<p>从**extranet**<p>和**未加入工作区**的设备<p>和从**AD Fabric**组<p>具有 MFA 的和<p>允许<p>**规则 #3**<p>从**extranet**<p>以及从已**加入工作区**的设备<p>和从**AD Fabric**组<p>允许|

## <a name="parameterized-policy-template-vs-non-parameterized-policy-template"></a>参数化策略模板与非参数化策略模板
访问控制策略可

参数化策略模板是具有参数的策略模板。 将此模板分配给 RPs.An 时，管理员需要输入这些参数的值。创建后，管理员无法对参数化策略模板进行更改。  参数化策略的一个示例是内置策略，允许特定组。  无论何时将此策略应用于 RP，都需要指定此参数。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP5.PNG)

非参数化策略模板是没有参数的策略模板。 管理员可以将此模板分配给 RPs，无需任何输入，并且可以在创建非参数化策略模板后对其进行更改。  这种情况的一个示例是内置策略，允许每个人和需要 MFA。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP4.PNG)

## <a name="how-to-create-a-non-parameterized-access-control-policy"></a>如何创建非参数化访问控制策略
若要创建非参数化的访问控制策略，请使用以下过程

#### <a name="to-create-a-non-parameterized-access-control-policy"></a>创建非参数化访问控制策略

1.  从左侧的 AD FS 管理 "中，选择" 访问控制策略 "，然后在右侧单击" 添加访问控制策略 "。

2.  输入名称和描述。  例如：允许具有经过身份验证的设备的用户。

3.  **如果满足以下任一规则**，则在 "允许访问" 下单击 "**添加**"。

4.  在 "允许" 下，选中 "**从具有特定信任级别的设备**" 旁边的框

5.  在底部选择带下划线的**特定**

6.  从弹出的窗口中，选择 "**通过**下拉"。  单击“确定” 。

    ![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP6.PNG)

7.  单击“确定” 。 单击“确定” 。

    ![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP7.PNG)

## <a name="how-to-create-a-parameterized-access-control-policy"></a>如何创建参数化访问控制策略
若要创建参数化访问控制策略，请使用以下过程

#### <a name="to-create-a-parameterized-access-control-policy"></a>创建参数化访问控制策略

1.  从左侧的 AD FS 管理 "中，选择" 访问控制策略 "，然后在右侧单击" 添加访问控制策略 "。

2.  输入名称和描述。  例如：允许具有特定声明的用户。

3.  **如果满足以下任一规则**，则在 "允许访问" 下单击 "**添加**"。

4.  在 "允许" 下，选中 "**包含请求中的特定声明**" 旁边的框

5.  在底部选择带下划线的**特定**

6.  在弹出的窗口中，选择 **"分配访问控制策略时指定的参数"**。  单击“确定” 。

    ![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP8.PNG)

7.  单击“确定” 。 单击“确定” 。

    ![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP9.PNG)

## <a name="how-to-create-a-custom-access-control-policy-with-an-exception"></a>如何使用例外创建自定义访问控制策略
若要创建具有例外的访问控制策略，请使用以下过程。

#### <a name="to-create-a-custom-access-control-policy-with-an-exception"></a>使用异常创建自定义访问控制策略

1.  从左侧的 AD FS 管理 "中，选择" 访问控制策略 "，然后在右侧单击" 添加访问控制策略 "。

2.  输入名称和描述。  例如：允许具有经过身份验证但未被管理的设备的用户。

3.  **如果满足以下任一规则**，则在 "允许访问" 下单击 "**添加**"。

4.  在 "允许" 下，选中 "**从具有特定信任级别的设备**" 旁边的框

5.  在底部选择带下划线的**特定**

6.  从弹出的窗口中，选择 "**通过**下拉"。  单击“确定” 。

7.  在 "例外" 下，选中 "**从具有特定信任级别的设备**" 旁边的框

8.  在底部的 "例外" 下，选择带下划线的**特定**

9. 从弹出的窗口中，选择 "**管理**"。  单击“确定” 。

10. 单击“确定” 。 单击“确定” 。

    ![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP10.PNG)

## <a name="how-to-create-a-custom-access-control-policy-with-multiple-permit-conditions"></a>如何创建具有多个允许条件的自定义访问控制策略
若要创建具有多个允许条件的访问控制策略，请使用以下过程

#### <a name="to-create-a-parameterized-access-control-policy"></a>创建参数化访问控制策略

1.  从左侧的 AD FS 管理 "中，选择" 访问控制策略 "，然后在右侧单击" 添加访问控制策略 "。

2.  输入名称和描述。  例如：允许具有特定声明和来自特定组的用户。

3.  **如果满足以下任一规则**，则在 "允许访问" 下单击 "**添加**"。

4.  在 "允许" 下，选中 "**从特定组**中" 旁边的框，并在**请求中使用特定声明**

5.  在底部，选择 "组"**旁边的第**一个条件的下划线

6.  在弹出的窗口中，选择 **"分配策略时指定的参数"**。  单击“确定” 。

7.  在底部，为第二个条件选择带下划线的**特定**"声明"

8.  在弹出的窗口中，选择 **"分配访问控制策略时指定的参数"**。  单击“确定” 。

9. 单击“确定” 。 单击“确定” 。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP12.PNG)

## <a name="how-to-assign-an-access-control-policy-to-a-new-application"></a>如何向新应用程序分配访问控制策略
向新应用程序分配访问控制策略非常直接，现已集成到用于添加 RP 的向导中。  在信赖方信任向导中，可以选择要分配的访问控制策略。  这是创建新的信赖方信任时的要求。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP13.PNG)

## <a name="how-to-assign-an-access-control-policy-to-an-existing-application"></a>如何将访问控制策略分配给现有应用程序
向现有应用程序分配访问控制策略只需从信赖方信任中选择应用程序，并在右击 "**编辑访问控制策略**"。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP14.PNG)

在此处，你可以选择访问控制策略并将其应用于应用程序。

![访问控制策略](media/Access-Control-Policies-in-AD-FS/ADFSACP15.PNG)

## <a name="see-also"></a>另请参阅
[AD FS 操作](../ad-fs-operations.md)
