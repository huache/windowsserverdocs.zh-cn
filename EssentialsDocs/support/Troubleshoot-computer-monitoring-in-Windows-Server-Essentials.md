---
title: 解决在 Windows Server Essentials 中监视计算机的问题
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: f1e6b377-4a24-4d28-9b25-05910914826b
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 55daffa3c1db284d3772fa39eb64e0411ad1c7a6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625094"
---
# <a name="troubleshoot-computer-monitoring-in-windows-server-essentials"></a>解决在 Windows Server Essentials 中监视计算机的问题

> 适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本主题提供有关在警报查看器中监视计算机的运行状况状态和通过 Windows Server Essentials 中的电子邮件通知监视计算机的运行状况的问题的疑难解答。

> [!NOTE]
> 有关 Windows Server Essentials 社区中的最新疑难解答信息，建议访问 [Windows Server Essentials 论坛](/answers/topics/windows-server-essentials.html)。 Windows Server Essentials 论坛是寻求帮助或提出问题的好地方。

## <a name="troubleshooting-email-notifications-for-alerts"></a>警报的电子邮件通知疑难解答

 本部分列出了在使用警报的电子邮件通知时可能遇到的各种问题。

### <a name="cannot-send-the-test-email-for-the-alert"></a>无法发送警报的测试电子邮件

 **问题** 收到一条错误消息，显示 "无法发送警报的测试电子邮件"。

 **原因** 警报通知设置中的以下任一问题都可能导致此错误：

- 不正确的 SMTP 服务器名称或端口号。

- 未正确指定 SMTP 服务器需要一个套接字层 (SSL) 连接。

- SMTP 服务器需要身份验证，但输入了错误的凭据。

  **解决方案** 更正电子邮件通知设置中的任何错误。

#### <a name="to-identify-issues-in-your-email-notification-settings"></a>标识电子邮件通知设置中的问题

- 向 Internet 服务提供商 (ISP) 询问正确的 SMTP 服务器名称、端口号和 SSL 用法。

- 在此位置中查看日志文件，以了解服务器上警报的电子邮件通知：

    ` %ProgramData%\Microsoft\Windows Server\Logs\SharedServiceHost-AlertServiceConfig.log`

    > [!TIP]
    > 若要查看 ProgramData 文件夹，必须显示隐藏的项目。 如果看不到 ProgramData 文件夹，请在功能区的 " **视图** " 选项卡上的 " **显示/隐藏** " 组中，选择 " **隐藏项** " 文本框。

#### <a name="to-update-your-email-notification-setup-for-alerts"></a>更新警报的电子邮件通知

1. 在仪表板上，单击右上角的任意警报图标以打开警报查看器。

2. 在警报查看器的底部，单击“设置警报的电子邮件通知”****。

3. 在“设置警报的电子邮件通知”**** 对话框中，单击“启用”****。

4. 在“SMTP 设置”**** 对话框中，更新 SMTP 设置，然后单击“确定”****。

5. 若要测试更新的设置，请单击“应用并发送电子邮件”****。

6. 在验证已成功发送测试电子邮件后，单击“确定”**** 以保存已更新的设置。

### <a name="test-email-notification-does-not-list-any-alerts"></a>测试电子邮件通知不列出任何警报

**问题** 虽然警报查看器中列出了警报，但警报的测试电子邮件通知不显示任何警报。

**解决方案** 并不是警报查看器中报告的所有警报都会生成电子邮件通知。 只有在其运行状况定义文件内配置为升级至电子邮件通知的警报，才会作为电子邮件发送到指定电子邮件收件人。

当你单击“应用和发送电子邮件”**** 时，通常将收到未列出任何运行状况警报的示例电子邮件通知。 但是，如果在此测试过程中标识了某个配置为发送电子邮件通知的运行状况警报，则该警报将包含在测试电子邮件中。

### <a name="active-alerts-are-displayed-for-an-uninstalled-application"></a>为已卸载的应用程序显示活动警报

**问题** 虽然应用程序和其运行状况定义文件已卸载，但仍显示该应用程序的活动警报。

**解决方案** 你必须手动删除已卸载应用程序的活动警报。 若要删除警报，请执行以下操作。

#### <a name="to-delete-an-alert-from-the-server-by-using-the-dashboard"></a>使用仪表板从服务器中删除警报

1. 在服务器上，打开仪表板。

2. 在导航窗格中，单击任意显示的警报图标（关键、警告或信息性）。 这将启动警报查看器。

3. 在警报查看器中，右键单击你要删除的警报，然后单击“删除此警报”****。