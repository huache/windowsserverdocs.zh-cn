---
ms.assetid: 3d770385-9834-4ebe-b66c-b684e0245971
title: 创建规则以根据传入声明允许或拒绝用户
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c6d0d1b2d91b4b0983dbe8169e094403bb2c732a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87967274"
---
# <a name="create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim"></a>创建规则以根据传入声明允许或拒绝用户


在 Windows Server 2016 中，可以使用**访问控制策略**来创建一个规则，该规则将根据传入声明允许或拒绝用户。  在 Windows Server 2012 R2 中，使用 "**基于传入声明的用户允许或拒绝用户**" 规则模板 Active Directory 联合身份验证服务 \( AD FS 中 \) ，你可以创建一个授权规则，该规则将根据传入声明的类型和值授予或拒绝用户对信赖方的访问权限。

例如，你可以使用它来创建一个规则，该规则仅允许具有组声明值为域管理员的用户访问信赖方。 如果希望允许所有用户访问信赖方，请使用 "**允许每个人**访问控制策略" 或 "**允许所有用户**" 规则模板，具体取决于你的 Windows Server 版本。 有权从联合身份验证服务访问信赖方的用户可能仍会被信赖方拒绝服务。

你可以使用以下过程通过 AD FS 管理 "管理单元来创建声明规则 \- 。

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

## <a name="to-create-a-rule-to-permit-users-based-on-an-incoming-claim-on-windows-server-2016"></a>创建规则以允许基于 Windows Server 2016 上的传入声明的用户

1.  在服务器管理器中，单击“工具”，选择“AD FS 管理”********。

2.  在控制台树中的 " **AD FS**下，单击"**访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny3.PNG)

3. 右键单击并选择 "**添加访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny4.PNG)

4. 在 "名称" 框中，输入策略的名称和说明，然后单击 "**添加**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny5.PNG)

5. 在**规则编辑器**中，在 "用户" 下，将 **"签入" 与请求中的特定声明**放在一起，并单击底部的**带下划线。**
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny6.PNG)

6. 在 "**选择声明**" 屏幕上，单击 "**声明**" 单选按钮，选择**声明类型**、**操作员**和**声明值**，然后单击 **"确定"**。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny7.PNG)

7.  在**规则编辑器**中，单击 **"确定"**。  在 "**添加访问控制策略**" 屏幕上，单击 **"确定"**。

8. 在**AD FS 管理**控制台树的 " **AD FS**下，单击"**信赖方信任**"。
![创建规则](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)

9.  右键单击要允许访问的**信赖方信任**，然后选择 "**编辑访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-All-Users/permitall2.PNG)

10. 在 "访问控制策略" 中选择策略，然后单击 "**应用** **" 和 "确定"**。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny8.PNG)

## <a name="to-create-a-rule-to-deny-users-based-on-an-incoming-claim-on-windows-server-2016"></a>创建规则以在 Windows Server 2016 上基于传入声明拒绝用户

1.  在服务器管理器中，单击“工具”，选择“AD FS 管理”********。

2.  在控制台树中的 " **AD FS**下，单击"**访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny3.PNG)

3. 右键单击并选择 "**添加访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny4.PNG)

4. 在 "名称" 框中，输入策略的名称和说明，然后单击 "**添加**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny9.PNG)

5. 在**规则编辑器**中，确保选中 "所有人"，并在 "**除了**将签入" 选项设置为**请求中的特定声明**下，单击底部的**带下划线。**
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny10.PNG)

6. 在 "**选择声明**" 屏幕上，单击 "**声明**" 单选按钮，选择**声明类型**、**操作员**和**声明值**，然后单击 **"确定"**。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny11.PNG)

7.  在**规则编辑器**中，单击 **"确定"**。  在 "**添加访问控制策略**" 屏幕上，单击 **"确定"**。

8. 在**AD FS 管理**控制台树的 " **AD FS**下，单击"**信赖方信任**"。
![创建规则](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)

9.  右键单击要允许访问的**信赖方信任**，然后选择 "**编辑访问控制策略**"。
![创建规则](media/Create-a-Rule-to-Permit-All-Users/permitall2.PNG)

10. 在 "访问控制策略" 中选择策略，然后单击 "**应用** **" 和 "确定"**。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny12.PNG)


## <a name="to-create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim-on-windows-server-2012-r2"></a>创建规则以根据 Windows Server 2012 R2 上的传入声明允许或拒绝用户

1.  在服务器管理器中，单击“工具”，选择“AD FS 管理”********。

2.  在控制台树中的 " **AD FS \\ 信任关系" " \\ 信赖方信任**" 下，单击列表中要创建此规则的特定信任。

3.  右键 \- 单击所选的信任，然后单击 "**编辑声明规则**"。
![创建规则](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG)

4.  在 "**编辑声明规则**" 对话框中，单击 "**颁发授权规则**" 选项卡或基于所需的授权规则类型的 "**委派授权规则**" 选项卡 \( \) ，然后单击 "**添加规则**" 以启动 "**添加授权声明规则向导**"。
![创建规则](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)

5.  在 "**选择规则模板**" 页上的 "**声明规则模板**" 下，选择 "**根据传入声明允许或拒绝用户**" 列表中的用户，然后单击 "**下一步**"。
![创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny1.PNG)

6.  在 "**声明规则名称**" 下的 "**配置规则**" 页上，在 "**传入声明类型**" 中选择声明类型在列表中，在 "**传入声明值**" 下键入一个值，或单击 "浏览" （如果可用），然后选择 \( \) 以下选项之一，具体取决于你的组织的需求：

    -   **允许具有此传入声明的用户访问**

    -   **拒绝具有此传入声明** 
 ![ 的用户访问权限创建规则](media/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim/permitdeny2.PNG)
7.  单击“完成”。

8.  在 "**编辑声明规则**" 对话框中，单击 **"确定"** 保存规则。

## <a name="additional-references"></a>其他参考
[配置声明规则](Configure-Claim-Rules.md)

[清单：为信赖方信任创建声明规则](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578(v=ws.11))

[何时使用授权声明规则](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)

[声明的角色](../../ad-fs/technical-reference/The-Role-of-Claims.md)

[声明规则的角色](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)
