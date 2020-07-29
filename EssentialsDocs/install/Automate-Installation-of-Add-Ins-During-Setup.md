---
title: 在安装过程中自动安装加载项
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 2e6ff6e4-8d68-4d49-9e38-8088bc8bf95e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b75b201f655e13fd367bfedc523f5b21b8e88b43
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181503"
---
# <a name="automate-installation-of-add-ins-during-setup"></a>在安装过程中自动安装加载项

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="automate-installing-add-ins-during-setup"></a><a name="BKMK_AddIns"></a>在安装过程中自动安装外接程序
 若要在安装过程中安装加载项，请使用本文档的[创建用于运行后初始配置任务的 PostIC.cmd 文件](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md)部分中描述的 PostIC.cmd 方法。

 将以下项添加到你的 PostIC.cmd：

```
C:\Program Files\Windows Server\bin\Installaddin.exe <full path to wssx file> -q
```

 加载项现在支持预安装和自定义卸载步骤。

 预安装步骤在安装 addin.xml 中指定的所有 **.msi** 文件之前运行。 在交互模式下运行时，会显示进度对话框，但不会更改进度。 取消按钮在预安装阶段中会禁用。 若要实现预安装步骤，请在 addin.xml 中添加以下内容（直接位于软件包下）：

> [!NOTE]
>  xml 架构需要与以下一个架构完全匹配：

```
<Package xmlns="https://schemas.microsoft.com/WindowsServerSolutions/2010/03/Addins" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Id>...</Id>
  <Version>...</Version>
  <Name>...</Name>
  <Allow32BitOn64BitClients>...</Allow32BitOn64BitClients>
  <ServerBinary>...</ServerBinary>
  <ClientBinary32>...</ClientBinary32>
  <ClientBinary64>...</ClientBinary64>
  <SupportedSkus>...</SupportUrl>
  <SupportUrl>...</SupportUrl>
  <Location>...</Location>
  <PrivacyStatement>...</PrivacyStatement>
  <OtherBinaries>...</OtherBinaries>
  <Preinstall>
<Executable>exefile</Executable>
<NormalArgs>args-for-interactive-mode</NormalArgs>
<SilentArgs>args-for-silent-mode</SilentArgs>
<IgnoreExitCode>true</IgnoreExitCode>
  </Preinstall>
  <UninstallConfirm>...</UninstallConfirm>
</Package>
<¦>
<¦>
```

 其中 **exefile** 是加载项软件包中用于执行预安装步骤的可执行文件，必须指定。 **NormalArgs** 指定当使用交互模式时要在命令行中传递给 exefile 的参数。 在此模式中，exefile 可以弹出一些对话框用于用户交互。 **SilentArgs** 指定当使用静默模式时要在命令行中传递给 exefile 的参数（调用 installaddin.exe 时指定 -q）。 exefile 文件在此模式下不应弹出任何窗口。 如果将 **IgnoreExitCode** 指定为 true，则会始终将预安装步骤视为成功，否则退出代码 0 指示成功，1 指示取消，其他值指示失败。 标记 **NormalArgs**、**SilentArgs** 和 **IgnoreExitCode** 都是可选的。

 可以将自定义卸载步骤用于以下任何任务：

- 替换内置确认对话框。

- 在卸载之前填充自定义对话框。

- 在卸载之前执行特定任务。

  若要实现卸载步骤，请在 addin.xml 中添加以下内容（直接位于软件包下）：

```
<Package xmlns="https://schemas.microsoft.com/WindowsServerSolutions/2010/03/Addins" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Id>...</Id>
  <Version>...</Version>
  <Name>...</Name>
  <Allow32BitOn64BitClients>...</Allow32BitOn64BitClients>
  <ServerBinary>...</ServerBinary>
  <ClientBinary32>...</ClientBinary32>
  <ClientBinary64>...</ClientBinary64>
  <SupportedSkus>...</SupportUrl>
  <SupportUrl>...</SupportUrl>
  <Location>...</Location>
  <PrivacyStatement>...</PrivacyStatement>
  <OtherBinaries>...</OtherBinaries>
  <Preinstall>¦</Preinstall>
<UninstallConfirm>
<Executable>full-path-to-exefile</Executable>
<Arguments>command-line-arguments</Arguments>
</UninstallConfirm>
</Package>
```

 其中 **full-path-to-exefile** 指定已安装在系统中的 exefile。 **Arguments** 可选，为 exefile 指定命令行参数。 在弹出内置卸载确认对话框之前调用 exefile。

 exefile 可在此阶段执行以下任务：

- 弹出一些对话框用于用户交互。

- 执行一些后台任务。

  此 exe 文件的退出代码确定卸载过程如何继续：

- 0：卸载过程继续进行，而不填充内置确认对话框，正如用户已确认一样。 （此方法可以用于替换内置确认对话框）；

- 1：取消卸载过程，最后会向用户显示已取消消息。 所有内容都保持不变；

- 其他：卸载过程继续进行，会出现内置确认对话框，正如不存在自定义卸载步骤一样。

  调用 exefile 时出现的任何故障都会产生与 exefile 返回非 0 和 1 的代码相同的行为。

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)