---
title: 利用事件对用户配置文件进行故障排除
description: 如何利用事件和跟踪日志对加载和卸载用户配置文件时的问题进行故障排除。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 04/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 9e927a77627e786015a928d798aafee13a2cc34b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394379"
---
# <a name="troubleshoot-user-profiles-with-events"></a>利用事件对用户配置文件进行故障排除

>适用于：Windows 10、Windows 8、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 和 Windows Server（半年频道）。

本主题讨论如何利用事件和跟踪日志对加载和卸载用户配置文件时的问题进行故障排除。 以下部分介绍如何使用记录用户配置文件信息的三个事件日志。

## <a name="step-1-checking-events-in-the-application-log"></a>步骤 1：检查应用程序日志中的事件

排查加载和卸载用户配置文件（包括漫游用户策略文件）问题的第一步是，使用事件查看器来检查应用程序日志中用户配置文件服务所记录的任何警告和错误事件。

下面介绍了如何在应用程序日志中查看用户配置文件服务事件：

1. 启动事件查看器。 要执行此操作，请打开“控制面板”，选择“系统和安全”，然后在“管理工具”部分选择“查看事件日志”     。 “事件查看器”窗口将打开。
2. 在控制台树中，依次导航到“Windows 日志”、“应用程序”   。
3. 在“操作”窗格中，选择“筛选当前日志”  。 “筛选当前日志”对话框将打开。
4. 在“事件资源”框中，选择“用户配置文件服务”复选框，然后选择“确定”    。
5. 查看事件列表，特别注意错误事件。
6. 如果发现值得注意的事件，请选择“事件日志联机帮助”链接以显示其他信息和故障排除过程。
7. 若要执行进一步的故障排除，请记下值得注意的事件的日期和时间，然后检查运行日志（如步骤 2 所述），查看有关用户配置文件服务在发生错误或警告事件时的操作的详细信息。

>[!NOTE]
>可以放心地忽略用户配置文件服务事件 1530“Windows 检测到你的注册表文件仍由其他应用程序或服务使用”。

## <a name="step-2-view-the-operational-log-for-the-user-profile-service"></a>步骤 2：查看用户配置文件服务的运行日志

如果无法单独使用应用程序日志来解决问题，请使用以下过程在运行日志中查看“用户配置文件服务”事件。 此日志显示服务的一些内部工作内容，并可帮助确定在配置文件加载或卸载过程中出现问题的位置。

默认情况下，Windows 应用程序日志和用户配置文件服务运行日志在所有 Windows 安装中都处于启用状态。

下面介绍了如何查看用户配置文件服务的运行日志：

1. 在事件查看器控制台树中，依次导航到“应用程序和服务日志”、“Microsoft”、“Windows”、“用户配置文件服务”和“运行”      。
2. 检查在应用程序日志中记下错误或警告事件前后发生的事件。

## <a name="step-3-enable-and-view-analytic-and-debug-logs"></a>步骤 3:启用和查看分析和调试日志

如果需要运行日志所提供信息外的更多详细信息，可以在受影响的计算机上启用分析和调试日志。 此级别的日志记录更详细，除非尝试排查问题，否则应将其禁用。

下面介绍如何启用和查看分析和调试日志：

1. 在事件查看器的“操作”窗格中，选择“查看”，然后选择“显示分析和调试日志”    。
2. 依次导航到“应用程序和服务日志”、“Microsoft”、“Windows”、“用户配置文件服务”和“诊断”      。
3. 选择“启用日志”，然后选择“是”   。 这将启用诊断日志，该日志将开始记录。
4. 如果需要更详细的信息，请参阅[步骤 4：创建和解码跟踪](#step-4-creating-and-decoding-a-trace)，获取有关如何创建跟踪日志的详细信息。
5. 完成问题排查后，导航到“诊断”日志，依次选择“禁用日志”、“查看”，然后清除“显示分析和调试日志”复选框，以隐藏分析并调试日志记录     。

## <a name="step-4-creating-and-decoding-a-trace"></a>步骤 4：创建和解码跟踪

如果无法利用事件解决问题，可以在该问题重现时创建跟踪日志（ETL 文件），然后使用 Microsoft 符号服务器中的公共符号对其进行解码。 跟踪日志提供有关用户配置文件服务正在执行的操作的非常具体的信息，并且可以帮助确定发生故障的位置。

使用 ETL 跟踪时，最好的策略是首先捕获尽可能小的日志。 日志解码后，搜索日志以查找故障。

下面介绍如何为用户配置文件服务创建和解码跟踪：

1. 使用本地管理员组的成员帐户登录用户遇到问题的计算机。
2. 在提升的命令提示符下，输入以下命令，其中 \<Path\> 是之前创建的本地文件夹的路径，例如 C:\\logs  ：
        
    ```PowerShell
    logman create trace -n RUP -o <Path>\RUP.etl -ets
    logman update RUP -p {eb7428f5-ab1f-4322-a4cc-1f1a9b2c5e98} 0x7FFFFFFF 0x7 -ets
    ```
3. 从“开始”屏幕中，选择用户名，然后选择“切换帐户”，请注意不要注销管理员  。 如果使用远程桌面，请关闭管理员会话以建立用户会话。
4. 重现问题。 重现此问题的过程通常是以遇到问题的用户身份登录、注销用户或两者都执行。
5. 在重现该问题后，再次以本地管理员身份登录。
6. 在提升的命令提示符下运行以下命令，将日志保存到 ETL 文件中：
  
    ```PowerShell
    logman stop -n RUP -ets
    ```
7. 键入以下命令，将 ETL 文件导出到当前目录（可能是主文件夹或 %WINDIR%\\System32 文件夹）中的可读文件：
    
    ```PowerShell
    Tracerpt <path>\RUP.etl
    ```
8. 打开“Summary.txt”文件和“Dumpfile.xml”文件（可以在 Microsoft Excel 中打开文件，以便更轻松地查看日志的完整详细信息）   。 查找包括“失败”或“已失败”的事件；可以放心地忽略包含“未知”事件名称的行    。

## <a name="more-information"></a>详细信息

* [部署漫游用户配置文件](deploy-roaming-user-profiles.md)