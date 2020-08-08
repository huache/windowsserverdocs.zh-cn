---
title: 应将副本服务器配置为标识有权发送复制流量的特定主服务器
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 0aeb1f4b-2e75-430b-9557-fe64738c4992
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: be830780023ca07563d967f7d46f6c2db7749a68
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87948435"
---
# <a name="replica-servers-should-be-configured-to-identify-specific-primary-servers-authorized-to-send-replication-traffic"></a>应将副本服务器配置为标识有权发送复制流量的特定主服务器

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*配置后，此副本服务器接受来自所有主服务器的复制流量，并将其存储在单个位置。*

### <a name="impact"></a>影响
*所有主服务器的复制存储在一个位置，这可能会导致隐私或安全问题。*

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器为特定的主服务器创建新的授权条目，并为每个服务器指定不同的存储位置。您可以使用通配符将主服务器组合到每个授权条目的集合中。*

#### <a name="create-authorization-entries-using-hyper-v-manager"></a>使用 Hyper-v 管理器创建授权条目

1.  打开 Hyper-V 管理器。  (服务器管理器中，单击 "**工具**" "  >  **hyper-v 管理器**"。 ) 

2.  在主机列表中，右键单击所需的主机，然后单击 " **Hyper-v 设置**"。

3.  在导航窗格中，单击 "**复制配置**"。

4.  在 "**授权和存储**" 下，单击 **"允许从指定的服务器复制"**。

5.  在服务器列表下方，单击 "**添加**"。

6.  在 "**添加授权条目**：

    -   键入第一个服务器的完全限定名称。

    -   指定一个专用位置以仅存储该服务器的文件。

7.  单击“确定”。

8.  为每个主服务器重复上述步骤。

9. 再次单击 **"确定"** 以完成，然后关闭窗口。

### <a name="create-authorization-entries-using-windows-powershell"></a>使用 Windows PowerShell 创建授权条目

1.  打开 Windows PowerShell。 从桌面 (，单击 "开始"，然后开始键入**Windows PowerShell**。 ) 

2.  右键单击 " **Windows PowerShell** "，然后单击 "**以管理员身份运行**"。

3.  运行与下面类似的命令，替换：

    -   具有服务器的完全限定域名的 server01.domain01.contoso.com 的主服务器名称。

    -   你所在位置的 D:\ReplicaVMStorage 的位置。

    -   名为 DEFAULT 的信任组（如果已创建）。 否则，请使用默认值。

```
New-VMReplicationAuthorizationEntry server01.domain01.contoso.com D:\ReplicaVMStorage DEFAULT
```

## <a name="see-also"></a>另请参阅
[新-New-vmreplicationauthorizationentry](https://technet.microsoft.com/library/hh848606.aspx)



