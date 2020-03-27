---
title: 网络策略
description: 本主题概述了 Windows Server 2016 中的网络策略服务器的网络策略，并包括指向有关 NPS 的其他指南的链接。
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: e4a9b134-6d1d-40d7-a49c-5f46d5fdb419
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 4ee256184cd551c5f2c2fcdb8544e4d061ea2bf3
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315760"
---
# <a name="network-policies"></a>网络策略

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题来概述 NPS 中的网络策略。

>[!NOTE]
>除了本主题之外，还提供了以下网络策略文档。
> - [访问权限](nps-np-access.md)
> - [配置网络策略](nps-np-configure.md)

网络策略是一组条件、约束和设置，允许您指定授权谁连接到网络以及其可以或不可以连接的环境。

作为远程身份验证拨入用户服务（RADIUS）服务器处理连接请求时，NPS 对连接请求执行身份验证和授权。 在身份验证过程中，NPS 验证连接到网络的用户或计算机的身份。 在授权过程中，NPS 确定是否允许用户或计算机访问网络。

为了做出这些决定，NPS 使用在 NPS 控制台中配置的网络策略。 NPS 还会检查 Active Directory&reg; 域服务中的用户帐户的拨入属性 \(AD DS\) 执行授权。

## <a name="network-policies---an-ordered-set-of-rules"></a>网络策略-一组有序规则

可以将网络策略视为规则。 每个规则都具有一组条件和设置。 NPS 将规则的条件与连接请求的属性进行对比。 如果规则和连接请求之间出现匹配，则规则中定义的设置会应用于连接。

当在 NPS 中配置了多个网络策略时，它们是一组有序规则。 NPS 根据列表中的第一个规则检查每个连接请求，然后根据第二个规则进行检查，依次类推，直到找到匹配项为止。

每个网络策略都有一个**策略状态**设置，该设置允许您启用或禁用策略。 如果禁用网络策略，则授权连接请求时，NPS 不评估策略。

>[!NOTE]
>如果希望 NPS 在对连接请求执行授权时评估网络策略，则必须通过选中 "启用策略" 复选框来配置**策略状态**设置。

## <a name="network-policy-properties"></a>网络策略属性

每个网络策略都有四种类别的属性：

### <a name="overview"></a>概述

 这些属性允许你指定是否启用策略、策略是否授予或拒绝访问权限，以及连接请求是否需要特定的网络连接方法或网络访问服务器（NAS）类型。 概述属性还允许您指定是否忽略 AD DS 中用户帐户的拨入属性。 如果选择该选项，则 NPS 只使用网络策略中的设置来确定是否授权连接。


### <a name="conditions"></a>条件

 使用这些属性，可以指定为了匹配网络策略，连接请求所必须具有的条件；如果策略中配置的条件与连接请求匹配，则 NPS 将在网络策略中指定的设置应用于连接。 例如，如果将 NAS IPv4 地址指定为网络策略的条件，并且 NPS 从具有指定 IP 地址的 NAS 接收连接请求，则策略中的条件与连接请求匹配。 


### <a name="constraints"></a>约束

 约束是匹配连接请求所需的网络策略的附加参数。 如果连接请求与约束不匹配，则 NPS 自动拒绝该请求。 不同于 NPS 响应网络策略中的不符合条件时，如果约束不匹配，则 NPS 会拒绝连接请求，而不会评估其他网络策略。

### <a name="settings"></a>设置

 使用这些属性，可以指定在策略的所有网络策略条件都匹配时，NPS 应用于连接请求的设置。

使用 NPS 控制台添加新的网络策略时，必须使用新建网络策略向导。 使用向导创建网络策略之后，可以通过在 NPS 控制台中双击策略来自定义策略，以获取策略属性。

有关模式匹配语法指定网络策略属性的示例，请参阅[在 NPS 中使用正则表达式](nps-crp-reg-expressions.md)。

有关 NPS 的详细信息，请参阅[网络策略服务器（NPS）](nps-top.md)。
