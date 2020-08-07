---
ms.assetid: 22f53391-8c6a-4873-a1f4-08b4760ea621
title: 声明的角色
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: eb41b8168024a231282716e5edd0bc59554d7da6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937820"
---
# <a name="the-role-of-claims"></a>声明的角色

在基于声明的 \- 标识模型中，声明在联合身份验证过程中扮演 pivotal 角色，它们是确定所有基于 Web 的 \- 身份验证和授权请求结果的关键组件。 此模型支持组织以一种标准化方法跨安全和企业界限安全地投影数字标识和权限或*声明*。

## <a name="what-are-claims"></a>什么是声明？

作为其最简单的形式，声明*只是*用于 \( \) 授权访问 \- 位于 Internet 任意位置的基于声明的应用程序的示例、名称、标识、组和用户的声明。 每个语句对应于存储在声明中的*值*。

### <a name="how-claims-are-sourced"></a>如何获取声明来源

中的联合身份验证服务 Active Directory 联合身份验证服务 \( AD FS \) 定义哪些声明在联合伙伴之间交换。 但是，在它可以执行此操作前必须首先借助检索到的或计算的值填充或获取声明来源。 每个声明值表示用户、组或实体的值，并且以下列两种方式之一获取来源：

1.  从属性存储中检索构成声明的值时，例如，从 Active Directory 用户帐户的特性中检索销售部门的属性值时。 有关详细信息，请参阅[属性存储的角色](The-Role-of-Attribute-Stores.md)。

2.  在传入声明的值转换为另一个基于在规则中表示逻辑的值时。 例如，当具有域管理员值的传入声明作为传出声明发送之前，转换为管理员的新值时。 有关详细信息，请参阅[声明规则的角色](The-Role-of-Claim-Rules.md)。

声明可以包括电子 \- 邮件地址、用户主体名称 \( UPN \) 、组成员身份和其他帐户属性之类的值。

### <a name="how-claims-flow"></a>如何声明流

其他各方依赖于声明的值为他们托管的基于 Web 的 \- 应用程序执行授权任务。 在 AD FS 管理 "管理单元中，这些参与方称为"*依赖方*" \- 。 联合身份验证服务负责协调许多不同参与方之间的信任关系。 它设计用于处理和流动来自最初源声明（也称为 AD FS 管理 "管理单元中的*声明提供程序*）的组织的受信任声明交换，并将其传递 \- 给信赖方。 信赖方然后使用这些声明做出授权决定。

使用此过程的声明流称为*声明管道*。 通过声明管道的声明流有三个步骤：

1.  从声明提供方收到的声明按照声明提供方信任上的接受转换规则进行处理。 这些规则可确定哪些声明接受自声明提供方。

2.  接受转换规则的输出用作颁发授权规则的输入。 这些规则可确定是否允许用户访问信赖方。

3.  接受转换规则的输出用作颁发转换规则的输入。 这些规则可确定将发送到信赖方的声明。

有关详细信息，请参阅[声明管道的角色](The-Role-of-the-Claims-Pipeline.md)

### <a name="how-claims-are-issued"></a>声明颁发的方式

在编写声明规则时，声明规则的传入声明源根据是在声明提供方信任还是信赖方信任上编写规则而不同。 在为声明提供方信任编写声明规则时，传入声明是从受信任声明提供方发送到联合身份验证服务的声明。 在为信赖方信任编写规则时，传入声明是由适用的声明提供方信任的声明规则输出的声明。 有关传入声明和传出声明的详细信息，请参阅[声明管道的角色](The-Role-of-the-Claims-Pipeline.md)和[声明引擎的角色](The-Role-of-the-Claims-Engine.md)。

## <a name="what-are-claim-types"></a>什么是声明类型？

声明类型为声明值提供上下文。 它通常表示为统一资源标识符 \( URI \) 。 AD FS 可以支持任何声明类型，并在默认情况下使用下表中的声明类型进行配置。

|“属性”|描述|URI|
|--------|---------------|-------|
|电子 \- 邮件地址|用户的电子 \- 邮件地址|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ identity \/ 声明 \/ emailaddress|
|名|用户的给定名称|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ identity \/ 声明 \/ givenname|
|“属性”|用户的唯一的名称|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ 标识 \/ 声明 \/ 名称|
|UPN|用户的用户主体名称 \( UPN \)|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ 标识 \/ 声明 \/ upn|
|公用名|用户的公用名|http： \/ \/schemas.xmlSoap.org \/ 声明 \/ CommonName|
|AD FS 1.x 电子 \- 邮件地址|\-与 AD FS 1.1 或 ADFS 1.0 进行互操作时用户的电子邮件地址|http： \/ \/schemas.xmlSoap.org \/ 声明 \/ EmailAddress|
|组|用户是其成员的组|http： \/ \/schemas.xmlSoap.org \/ 声明 \/ 组|
|AD FS 1.x UPN|与 AD FS 1.1 或 ADFS 1.0 互操作时用户的 UPN|http： \/ \/schemas.xmlSoap.org \/ 声明 \/ UPN|
|角色|用户具有的角色|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ 角色|
|Surname|用户的姓氏|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ 标识 \/ 声明 \/ 姓氏|
|PPID|用户的专用标识符|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ identity \/ 声明 \/ privatepersonalidentifier|
|名称标识符|用户的 SAML 名称标识符|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ identity \/ 声明 \/ nameidentifier|
|身份验证方法|用于对用户进行身份验证的方法|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ authenticationmethod|
|“仅拒绝”组 SID|用户的 "仅拒绝" \- 组 SID|http： \/ \/schemas.xmlsoap.org \/ ws \/ 2005 \/ 05 \/ identity \/ 声明 \/ denyonlysid|
|“仅拒绝”主 SID|用户的 "仅拒绝" \- 主 SID|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ denyonlyprimarysid|
|“仅拒绝”主组 SID|用户的 "仅拒绝" \- 主组 SID|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ denyonlyprimarygroupsid|
|组 SID|用户的组 SID|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ groupsid|
|主组 SID|用户的主组 SID|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ primarygroupsid|
|主 SID|用户的主 SID|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ primarysid|
|Windows 帐户名|用户的域帐户名，格式为\<domain\>\\\<user\>|http： \/ \/ schemas.microsoft.com \/ ws \/ 2008 \/ 06 \/ 标识 \/ 声明 \/ windowsaccountname|

## <a name="what-are-claim-descriptions"></a>什么是声明说明？

声明说明表示 AD FS 支持且可在联合元数据中发布的声明类型的列表。 上表中提到的声明类型在 "AD FS 管理" 管理单元中配置为声明说明 \- 。

将发布到联合元数据的声明说明集合存储在 AD FS 配置数据库中。 这些声明说明用于联合身份验证服务的各个组件。

每个声明说明包括声明类型 URI、名称、发布状态和描述。 您可以使用 "AD FS 管理" 管理单元中的 "**声明说明**" 节点管理声明说明集合 \- 。 您可以使用管理单元修改声明说明的发布状态 \- 。 提供了下列设置：

- **在联合元数据中发布此声明作为此联合身份验证服务可以接受** \( 的声明类型"发布为已接受 \) "-指示此联合身份验证服务将接受的声明类型。

- **在联合元数据中发布此声明作为此联合身份验证服务可以发送** \( 的声明类型发布方式 \) -指示此联合身份验证服务提供的声明类型。 它们作为联合身份验证服务愿意发送的声明类型而发布给其他服务。 声明提供方发送的实际声明类型通常是此列表的子集。

有关如何设置声明类型的发布状态的详细信息，请参阅 AD FS 部署指南中的[添加声明说明](../operations/add-a-claim-description.md)。

### <a name="when-generating-federation-metadata"></a>在生成联合元数据时

联合元数据包括标记为发布的所有声明说明。

### <a name="when-claims-rules-are-processed"></a>在处理声明规则时

在你保存有关声明说明的配置信息时，你将更轻松地配置有关声明规则。 有关可以在声明提供方组织中使用的声明规则的详细信息，请参阅[声明规则的角色](The-Role-of-Claim-Rules.md)。
