---
title: 使用客户端访问许可证 (CAL) 许可 RDS 部署
description: 远程桌面服务中的客户端授权的概述。
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 5be6546b-df16-4475-bcba-aa75aabef3e3
author: lizap
ms.author: elizapo
ms.date: 02/12/2020
manager: dongill
ms.openlocfilehash: 295536afc77d0559fd7d2d4a22f555231a1aab75
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80858070"
---
# <a name="license-your-rds-deployment-with-client-access-licenses-cals"></a>使用客户端访问许可证 (CAL) 许可 RDS 部署

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016

连接到远程桌面会话主机的每个用户和设备需要客户端访问许可证 (CAL)。 使用 RD 授权来安装、颁发和跟踪 RDS CAL。  

当用户或设备连接到 RD 会话主机服务器时，RD 会话主机服务器将确定是否需要 RDS CAL。 然后，RD 会话主机服务器从远程桌面许可证服务器请求 RDS CAL。 如果可从许可证服务器获取相应的 RDS CAL，则会将 RDS CAL 颁发给客户端，并且客户端能够连接到 RD 会话主机服务器，并从此处连接到桌面或它们正在尝试使用的应用。

虽然在一个授权宽限期内不需要任何许可证服务器，但在此宽限期过后，客户端必须先具有由许可证服务器颁发的有效 RDS CAL，然后才能登录到 RD 会话主机服务器。

使用以下信息来了解客户端访问授权在远程桌面服务中的工作方式，以及部署和管理你的许可证：

- [使用客户端访问许可证 (CAL) 许可 RDS 部署](#license-your-rds-deployment-with-client-access-licenses-cals)
  - [了解 RDS CAL 模型](#understanding-the-rds-cal-model)
  - [RDS CAL 版本兼容性](#rds-cal-version-compatibility)

## <a name="understanding-the-rds-cal-model"></a>了解 RDS CAL 模型

有两种类型的 RDS CAL：

- RDS - 每设备 CAL
- RDS - 每用户 CAL

下表概述了两种类型的 CAL 之间的差异：

| 每设备                                                     | 每用户                                                                         |
|----------------------------------------------------------------|----------------------------------------------------------------------------------|
| RDS CAL 以物理方式分配给每个设备。                   | RDS CAL 分配给 Active Directory 中的用户。                                 |
| RDS CAL 由许可证服务器跟踪。                        | RDS CAL 由许可证服务器跟踪。                                          |
| 无论 Active Directory 成员身份为何，都可以跟踪 RDS CAL。 | 不能在工作组中跟踪 RDS CAL。                                       |
| 最多可以撤消 20% 的 RDS CAL。                              | 无法撤消任何 RDS CAL。                                                      |
| 临时 RDS CAL 的有效期为 52–89 天。                       | 临时 RDS CAL 不可用。                                                |
| 不能过度分配 RDS CAL。                                  | 可以过度分配 RDS CAL（这违反远程桌面许可协议）。 |

如果使用每设备模型，则在设备首次连接到 RD 会话主机时，会颁发临时许可证。 该设备第二次连接时，只要激活许可证服务器，并且存在可用 RDS CAL，许可证服务器就会按设备 CAL 颁发永久的 RDS。

如果使用每用户模型，则不会强制执行授权，并向每个用户授予从任意数量的设备连接到 RD 会话主机的许可证。 许可证服务器颁发来自可用的 RDS CAL 池或过度使用的 RDS CAL 池的许可证。 你必须负责确保你的所有用户具有有效的许可证且没有过度使用的 CAL；否则，你违反了远程桌面服务许可条款。

若要确保遵守远程桌面服务许可条款，请跟踪组织中使用的每用户 CAL 的 RDS 数，确保每用户 CAL 有足够的 RDS 安装在所有用户的许可证服务器上。

可以使用远程桌面授权管理器跟踪并生成有关 RDS - 每用户 CAL 的报告。

## <a name="rds-cal-version-compatibility"></a>RDS CAL 版本兼容性

用户或设备的 RDS CAL 必须兼容用户或设备连接到的 Windows Server 的版本。 不能使用较低版本的 RDS CAL 来访问较高版本的 Windows Server，但可以使用较高版本的 RDS CAL 来访问较低版本的 Windows Server。 例如，若要连接到 Windows Server 2016 RD 会话主机，需要使用 RDS 2016 CAL 或更高版本，而若要连接到 Windows Server 2012 R2 RD 会话主机，则需要使用 RDS 2012 CAL 或更高版本。

下表显示了哪些 RDS CAL 和 RD 会话主机版本彼此兼容。

|                  | RDS 2008 R2 及更低版本的 CAL | RDS 2012 CAL | RDS 2016 CAL | RDS 2019 CAL |
|---------------------------------|--------|--------|--------|--------|
| **2008、2008 R2 会话主机** | 是    | 是    | 是    | 是     |
| **2012 会话主机**         | 否     | 是    | 是    | 是    |
| **2012 R2 会话主机**      | 否     | 是    | 是    | 是    |
| **2016 会话主机**         | 否     | 否     | 是    | 是    |
| **2019 会话主机**         | 否     | 否     | 否     | 是    |

必须在兼容的 RD 许可证服务器上安装 RDS CAL。 任何 RDS 许可证服务器都可以托管来自所有以前版本的远程桌面服务和当前版本的远程桌面服务的许可证。 例如，Windows Server 2016 RDS 许可证服务器可以托管来自所有以前版本的 RDS 的许可证，而 Windows Server 2012 R2 RDS 许可证服务器最多只能托管来自 Windows Server 2012 R2 的许可证。

下表显示了哪些 RDS CAL 和许可证服务器版本彼此兼容。

|                  | RDS 2008 R2 及更低版本的 CAL | RDS 2012 CAL | RDS 2016 CAL | RDS 2019 CAL |
|---------------------------------|--------|--------|--------|--------|
| **2008、2008 R2 许可证服务器** | 是    | 否   | 否   | 否    |
| **2012 许可证服务器**         | 是     | 是    | 否   | 否    |
| **2012 R2 许可证服务器**      | 是     | 是    | 否   | 否    |
| **2016 许可证服务器**         | 是     | 是    | 是   | 否    |
| **2019 许可证服务器**         | 是     | 是    | 是  | 是   |
