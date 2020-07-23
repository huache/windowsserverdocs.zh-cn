---
ms.assetid: a33bd54c-e6db-4b58-8264-c0f34bd8ba39
title: 演练-Workplace Join 到 Android 设备
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 8db10b43a2511cb5e16609e36c9356c853b93bfc
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966889"
---
# <a name="walkthrough-workplace-join-to-an-android-device"></a>演练： Workplace Join 到 Android 设备



## <a name="join-your-device-with-workplace-join"></a>使用“工作区加入”加入你的设备

> [!NOTE]
> Android 工作区加入要求 Azure Active Directory 设备注册服务。 若要在本地强制实施条件设备策略，必须在启用设备对象写回选项的情况下部署目录同步工具（DirSync）。 目前，设备写回 Active Directory 从 Azure Active Directory 可能需要长达3小时的时间。 因此，在创建工作帐户后，用户必须等待3小时才能访问本地 web 应用程序。 有关部署 Azure Active Directory 设备注册服务的详细信息，请参阅[Azure Active Directory 设备注册服务概述](/previous-versions/azure/dn788908(v=azure.100))

#### <a name="create-a-work-account-that-joins-your-device-with-workplace-join"></a>创建一个工作帐户，用于将设备加入工作区加入

1.  需要在设备上安装 Azure Authenticator 的应用程序，以创建一个工作帐户，该帐户将设备加入到工作区加入。 以下 URL 提供了有关如何在 Android 设备上安装 Azure 验证器应用程序并添加工作帐户的说明。 工作帐户会使你的 Android 设备进入受信任的设备，并为设备上的应用程序提供单一登录（SSO）。 你可以使用受信任的设备访问 web 应用程序和现代业务线应用程序，如你的 IT 管理员的建议。 有关详细信息，请参阅[适用于 Android 的 Azure Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)。

## <a name="see-also"></a>另请参阅
[跨公司应用程序从任何设备加入工作区以实现 SSO 和无缝第二重身份验证](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md) 
[使用 Azure Active Directory 设备注册服务设置本地条件性访问](/azure/active-directory/active-directory-device-registration-on-premises-setup)
