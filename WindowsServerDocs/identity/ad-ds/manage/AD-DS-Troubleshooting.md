---
ms.assetid: fd3bc84a-48eb-4f00-9dc2-846bf2c2668b
title: AD DS 故障排除
description: AD DS 的故障排除部分概述
ms.author: joflore
author: MicrosoftGuyJFlo
manager: dcscontentpm
ms.date: 11/22/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: b9e1cf812234bc3b0bd81db7045ed83208f3a0ff
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80824360"
---
# <a name="ad-ds-troubleshooting"></a>AD DS 故障排除

>适用于： Windows Server 2019、Windows Server 2016、Windows Server 2012 R2

本部分包含诊断和解决 Active Directory 复制期间可能出现的问题的疑难解答建议和步骤。 它重点介绍如何响应目录服务事件日志条目，以及如何解释 Repadmin 和 Dcdiag.exe 等工具可能会报告的消息。

对于运行 Windows Server 2012 R2 或更高版本的所有域控制器，Repadmin 和 Dcdiag.exe 都可用。 有关如何使用这些工具来解决问题的详细信息，请参阅以下文章。

- [配置计算机以进行故障排除 Active Directory](../manage/troubleshoot/Configuring-a-Computer-for-Troubleshooting.md)
- [Active Directory 复制问题疑难解答](../manage/troubleshoot/Troubleshooting-Active-Directory-Replication-Problems.md)

另一种有用的技术是 Windows 事件跟踪（ETW）。 您可以使用 ETW 对域控制器之间的 LDAP 通信进行故障排除。 有关详细信息，请参阅[使用 ETW 排查 LDAP 连接问题](../manage/troubleshoot/troubleshoot-ldap-using-etw.md)。

你还可以在运行 Windows 10 的成员服务器上安装远程服务器管理工具（RSAT）。 有关如何安装 RSAT 的信息，请参阅[远程服务器管理工具](https://docs.microsoft.com/windows-server/remote/remote-server-administration-tools)。
