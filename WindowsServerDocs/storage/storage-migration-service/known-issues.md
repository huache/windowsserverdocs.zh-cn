---
title: 存储迁移服务的已知问题
description: 有关存储迁移服务的已知问题和疑难解答支持，如如何为 Microsoft 支持部门收集日志。
author: nedpyle
ms.author: nedpyle
manager: tiaascs
ms.date: 07/29/2020
ms.topic: article
ms.openlocfilehash: ea138d8bb0b804ae4d08ed6ffe330e9714af43f3
ms.sourcegitcommit: 2b1a12c85acff137e5ac84cd0e62d8353fcdde31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89087480"
---
# <a name="storage-migration-service-known-issues"></a>存储迁移服务的已知问题

本主题包含有关使用 [存储迁移服务](overview.md) 迁移服务器时的已知问题的解答。

存储迁移服务分为两部分： Windows Server 中的服务和 Windows 管理中心中的用户界面。 服务在 Windows Server、长期服务通道以及 Windows Server、半年通道中可用;虽然可单独下载 Windows 管理中心。 我们还会定期包括 Windows Server 累积更新中的更改（通过 Windows 更新发布）。

例如，Windows Server 版本1903包括存储迁移服务的新功能和修复程序，它们也可用于 Windows Server 2019 和 Windows Server，版本1809通过安装 [KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534)来实现。

## <a name="how-to-collect-log-files-when-working-with-microsoft-support"></a><a name="collecting-logs"></a> 如何在使用 Microsoft 支持部门时收集日志文件

存储迁移服务包含 Orchestrator 服务和代理服务的事件日志。 Orchestrator 服务器始终包含事件日志，并且安装了代理服务的目标服务器包含代理日志。 这些日志位于：

- 应用程序和服务日志 \ Microsoft \ Windows \ StorageMigrationService
- 应用程序和服务日志 \ Microsoft \ Windows \ StorageMigrationService-Proxy

如果需要收集这些日志以供脱机查看或发送到 Microsoft 支持部门，GitHub 上提供了一个开源 PowerShell 脚本：

 [存储迁移服务帮助器](https://aka.ms/smslogs)

查看自述文件的用法。

## <a name="storage-migration-service-doesnt-show-up-in-windows-admin-center-unless-managing-windows-server-2019"></a>除非管理 Windows Server 2019，否则不会在 Windows 管理中心中显示存储迁移服务

当使用1809版本的 Windows 管理中心来管理 Windows Server 2019 orchestrator 时，将看不到存储迁移服务的工具选项。

Windows 管理中心存储迁移服务扩展受版本限制，只管理 Windows Server 2019 1809 或更高版本的操作系统。 如果你使用它来管理较早的 Windows Server 操作系统或有问必答预览，则该工具将不会显示。 此行为是设计使然。

若要解决此问题，请使用或升级到 Windows Server 2019 build 1809 或更高版本。

## <a name="storage-migration-service-cutover-validation-fails-with-error-access-is-denied-for-the-token-filter-policy-on-destination-computer"></a>存储迁移服务转换验证失败，出现错误 "对目标计算机上的令牌筛选器策略的访问被拒绝"

运行切换验证时，收到错误 "失败：目标计算机上的令牌筛选器策略访问被拒绝"。 即使您为源计算机和目标计算机提供了正确的本地管理员凭据，也会出现这种情况。

此问题已在 [KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534) 更新中解决。

## <a name="storage-migration-service-isnt-included-in-windows-server-2019-evaluation-or-windows-server-2019-essentials-edition"></a>Windows Server 2019 评估版或 Windows Server 2019 Essentials edition 中不包含存储迁移服务

使用 Windows 管理中心连接到 [Windows server 2019 评估版](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019) 或 windows Server 2019 Essentials edition 时，没有管理存储迁移服务的选项。 角色和功能中也不包含存储迁移服务。

此问题是由 Windows Server 2019 和 Windows Server 2019 Essentials 的评估介质中的服务问题引起的。

若要解决此问题，请安装 Windows Server 2019 的零售、MSDN、OEM 或批量许可版本，但不要将其激活。 如果没有激活，Windows Server 的所有版本都将在评估模式下运行180天。

我们已在更高版本的 Windows Server 中解决了此问题。

## <a name="storage-migration-service-times-out-downloading-the-transfer-error-csv"></a>存储迁移服务下载传输错误 CSV 超时

使用 Windows 管理中心或 PowerShell 下载传输操作仅限错误的 CSV 日志时，收到错误消息：

```
Transfer Log - Please check file sharing is allowed in your firewall. : This request operation sent to net.tcp://localhost:28940/sms/service/1/transfer did not receive a reply within the configured timeout (00:01:00). The time allotted to this operation may have been a portion of a longer timeout. This may be because the service is still processing the operation or because the service was unable to send a reply message. Please consider increasing the operation timeout (by casting the channel/proxy to IContextChannel and setting the OperationTimeout property) and ensure that the service is able to connect to the client.
```

此问题是由存储迁移服务允许的默认一分钟超时内无法筛选的传输文件数过多引起的。

若要解决此问题，请执行以下操作：

1. 在 orchestrator 计算机上，使用 Notepad.exe 编辑 *% SYSTEMROOT% \SMS\Microsoft.StorageMigration.Service.exe.config* 文件，将 "sendTimeout" 的默认值从1分钟更改为10分钟

    ```
    <bindings>
      <netTcpBinding>
        <binding name="NetTcpBindingSms"
                 sendTimeout="00:10:00"
    ```

2. 重新启动 orchestrator 计算机上的 "存储迁移服务" 服务。

3. 在 orchestrator 计算机上，启动 Regedit.exe

4. 如果以下注册表子项尚不存在，请创建它：

    `HKEY_LOCAL_MACHINE\Software\Microsoft\SMSPowershell`

5. 在“编辑”菜单上，指向“新建”，然后单击“DWORD 值”。

6. 键入 "WcfOperationTimeoutInMinutes" 作为 DWORD 名称，然后按 ENTER。

7. 右键单击 "WcfOperationTimeoutInMinutes"，然后单击 "修改"。

8. 在 "基本数据" 框中，单击 "Decimal"

9. 在 "数值数据" 框中，键入 "10"，然后单击 "确定"。

10. 启动注册表编辑器。

11. 尝试再次下载错误的 CSV 文件。

如果要迁移的文件量非常大，则可能需要将此超时值提高到超过10分钟。 

## <a name="validation-warnings-for-destination-proxy-and-credential-administrative-privileges"></a>目标代理和凭据管理权限的验证警告

验证传输作业时，将看到以下警告：

```
The credential has administrative privileges.
Warning: Action isn't available remotely.
The destination proxy is registered.
Warning: The destination proxy wasn't found.
```

如果你尚未在 Windows Server 2019 目标计算机上安装存储迁移服务代理服务，或者目标计算机是 Windows Server 2016 或 Windows Server 2012 R2，则此行为是设计使然。 建议迁移到安装了代理的 Windows Server 2019 计算机以大幅提高传输性能。

## <a name="certain-files-dont-inventory-or-transfer-error-5-access-is-denied"></a>某些文件未列出清单或传输，错误 5 "拒绝访问"

当在源计算机和目标计算机上清点或传输文件时，用户已删除管理员组的权限的文件无法迁移。 检查存储迁移服务-代理调试显示：

```
Log Name: Microsoft-Windows-StorageMigrationService-Proxy/Debug
Source: Microsoft-Windows-StorageMigrationService-Proxy
Date: 2/26/2019 9:00:04 AM
Event ID: 10000
Task Category: None
Level: Error
Keywords:
User: NETWORK SERVICE
Computer: srv1.contoso.com
Description:

02/26/2019-09:00:04.860 [Error] Transfer error for \\srv1.contoso.com\public\indy.png: (5) Access is denied.
Stack Trace:
at Microsoft.StorageMigration.Proxy.Service.Transfer.FileDirUtils.OpenFile(String fileName, DesiredAccess desiredAccess, ShareMode shareMode, CreationDisposition creationDisposition, FlagsAndAttributes flagsAndAttributes)
at Microsoft.StorageMigration.Proxy.Service.Transfer.FileDirUtils.GetTargetFile(String path)
at Microsoft.StorageMigration.Proxy.Service.Transfer.FileDirUtils.GetTargetFile(FileInfo file)
at Microsoft.StorageMigration.Proxy.Service.Transfer.FileTransfer.InitializeSourceFileInfo()
     at Microsoft.StorageMigration.Proxy.Service.Transfer.FileTransfer.Transfer()
at Microsoft.StorageMigration.Proxy.Service.Transfer.FileTransfer.TryTransfer()
```

此问题的原因是存储迁移服务中的代码缺陷未调用备份权限。

若要解决此问题，请在 [KB4490481 （2019年4月2日）安装 Windows 更新在 orchestrator 计算机上安装 (OS Build 17763.404) ](https://support.microsoft.com/help/4490481/windows-10-update-kb4490481) ，并在目标计算机上安装代理服务。 请确保源迁移用户帐户是源计算机上的本地管理员和存储迁移服务协调器。 请确保目标迁移用户帐户是目标计算机上的本地管理员和存储迁移服务协调器。

## <a name="dfsr-hashes-mismatch-when-using-storage-migration-service-to-preseed-data"></a>使用存储迁移服务预先播种数据时，DFSR 哈希不匹配

当使用存储迁移服务将文件传输到新目标，然后将 DFS 复制配置为通过 preseeded 复制或 DFS 复制数据库克隆将该数据复制到现有服务器时，所有文件都将遇到哈希不匹配，并重新复制。 使用存储迁移服务传输数据流、安全流、大小和属性后，它们看起来完全匹配。 检查具有 ICACLS 的文件或 DFS 复制数据库克隆调试日志显示：

### <a name="source-file"></a>源文件
```
  icacls d:\test\Source:

  icacls d:\test\thatcher.png /save out.txt /t thatcher.png
  D:AI(A;;FA;;;BA)(A;;0x1200a9;;;DD)(A;;0x1301bf;;;DU)(A;ID;FA;;;BA)(A;ID;FA;;;SY)(A;ID;0x1200a9;;;BU)
```

### <a name="destination-file"></a>目标文件

```
  icacls d:\test\thatcher.png /save out.txt /t thatcher.png
  D:AI(A;;FA;;;BA)(A;;0x1301bf;;;DU)(A;;0x1200a9;;;DD)(A;ID;FA;;;BA)(A;ID;FA;;;SY)(A;ID;0x1200a9;;;BU)**S:PAINO_ACCESS_CONTROL**
```
### <a name="dfsr-debug-log"></a>DFSR 调试日志

```
   20190308 10:18:53.116 3948 DBCL  4045 [WARN] DBClone::IDTableImportUpdate Mismatch record was found.

   Local ACL hash:1BCDFE03-A18BCE01-D1AE9859-23A0A5F6
   LastWriteTime:20190308 18:09:44.876
   FileSizeLow:1131654
   FileSizeHigh:0
   Attributes:32

   Clone ACL hash:**DDC4FCE4-DDF329C4-977CED6D-F4D72A5B**
   LastWriteTime:20190308 18:09:44.876
   FileSizeLow:1131654
   FileSizeHigh:0
   Attributes:32
```

此问题由 [KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534) 更新修复。

## <a name="error-couldnt-transfer-storage-on-any-of-the-endpoints-when-transferring-from-windows-server-2008-r2"></a>从 Windows Server 2008 R2 传输时，出现错误 "无法传输任何终结点上的存储"

尝试从 Windows Server 2008 R2 源计算机传输数据时，不会传输任何数据，并且你会收到错误：

```
Couldn't transfer storage on any of the endpoints.
0x9044
```

如果 Windows Server 2008 R2 计算机没有通过 Windows 更新的所有重要更新和重要更新进行完全修补，则会出现此错误。 为了安全起见，保留 Windows Server 2008 R2 计算机的更新尤其重要，因为该操作系统不包含 Windows Server 的较新版本的安全改进。

## <a name="error-couldnt-transfer-storage-on-any-of-the-endpoints-and-check-if-the-source-device-is-online---we-couldnt-access-it"></a>错误： "无法在任何端点上传输存储" 和 "检查源设备是否处于联机状态-我们无法访问它"。

如果尝试从源计算机传输数据，则不会传输部分或全部共享，错误如下：

```
Couldn't transfer storage on any of the endpoints.
0x9044
```

检查 SMB 传输详细信息时显示错误：

```
Check if the source device is online - we couldn't access it.
```

检查 StorageMigrationService/Admin 事件日志显示：

```
Couldn't transfer storage.

Job: Job1
ID:
State: Failed
Error: 36931
Error Message:

Guidance: Check the detailed error and make sure the transfer requirements are met. The transfer job couldn't transfer any source and destination computers. This could be because the orchestrator computer couldn't reach any source or destination computers, possibly due to a firewall rule, or missing permissions.
```

检查 StorageMigrationService/Debug 日志显示：

```
07/02/2019-13:35:57.231 [Error] Transfer validation failed. ErrorCode: 40961, Source endpoint is not reachable, or doesn't exist, or source credentials are invalid, or authenticated user doesn't have sufficient permissions to access it.
at Microsoft.StorageMigration.Proxy.Service.Transfer.TransferOperation.Validate()
at Microsoft.StorageMigration.Proxy.Service.Transfer.TransferRequestHandler.ProcessRequest(FileTransferRequest fileTransferRequest, Guid operationId)
```

如果迁移帐户没有对 SMB 共享的至少读取权限，则这是一个代码缺陷。 此问题首先在累积更新 [4520062](https://support.microsoft.com/help/4520062/windows-10-update-kb4520062)中解决。

## <a name="error-0x80005000-when-running-inventory"></a>运行清单时出现错误0x80005000

安装 [KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534) 并尝试运行清单后，清单失败并出现错误：

```
EXCEPTION FROM HRESULT: 0x80005000

Log Name:      Microsoft-Windows-StorageMigrationService/Admin
Source:        Microsoft-Windows-StorageMigrationService
Date:          9/9/2019 5:21:42 PM
Event ID:      2503
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      FS02.TailwindTraders.net
Description:
Couldn't inventory the computers.
Job: foo2
ID: 20ac3f75-4945-41d1-9a79-d11dbb57798b
State: Failed
Error: 36934
Error Message: Inventory failed for all devices
Guidance: Check the detailed error and make sure the inventory requirements are met. The job couldn't inventory any of the specified source computers. This could be because the orchestrator computer couldn't reach it over the network, possibly due to a firewall rule or missing permissions.

Log Name:      Microsoft-Windows-StorageMigrationService/Admin
Source:        Microsoft-Windows-StorageMigrationService
Date:          9/9/2019 5:21:42 PM
Event ID:      2509
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      FS02.TailwindTraders.net
Description:
Couldn't inventory a computer.
Job: foo2
Computer: FS01.TailwindTraders.net
State: Failed
Error: -2147463168
Error Message:
Guidance: Check the detailed error and make sure the inventory requirements are met. The inventory couldn't determine any aspects of the specified source computer. This could be because of missing permissions or privileges on the source or a blocked firewall port.

Log Name:      Microsoft-Windows-StorageMigrationService-Proxy/Debug
Source:        Microsoft-Windows-StorageMigrationService-Proxy
Date:          2/14/2020 1:18:21 PM
Event ID:      10000
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      2019-rtm-orc.ned.contoso.com
Description:
02/14/2020-13:18:21.097 [Erro] Failed device discovery stage SystemInfo with error: (0x80005000) Unknown error (0x80005000)
```

当你以用户主体)  (名称（如 ""）的形式提供迁移凭据时，存储迁移服务中的代码缺陷会导致此错误 meghan@contoso.com 。 存储迁移服务协调器服务无法正确分析此格式，这导致在域查找中为 KB4512534 和19H1 中的群集迁移支持添加了故障。

若要解决此问题，请以 "域 \ 用户" 格式提供凭据，如 "Contoso\Meghan"。

## <a name="error-serviceerror0x9006-or-the-proxy-isnt-currently-available-when-migrating-to-a-windows-server-failover-cluster"></a>错误 "ServiceError0x9006" 或 "代理当前不可用"。 迁移到 Windows Server 故障转移群集时

尝试针对群集文件服务器传输数据时，会收到如下错误：

```
Make sure the proxy service is installed and running, and then try again. The proxy isn't currently available.
0x9006
ServiceError0x9006,Microsoft.StorageMigration.Commands.UnregisterSmsProxyCommand
```

如果文件服务器资源从其原始 Windows Server 2019 群集所有者节点移到新节点，并且该节点上未安装存储迁移服务代理功能，则会出现此错误。

作为一种解决方法，请将目标文件服务器资源移回首次配置传输配对时使用的原始所有者群集节点。

另一种解决方法：

1. 在群集中的所有节点上安装存储迁移服务代理功能。
2. 在 orchestrator 计算机上运行以下存储迁移服务 PowerShell 命令：

   ```PowerShell
   Register-SMSProxy -ComputerName <destination server> -Force
   ```
## <a name="error-dll-was-not-found-when-running-inventory-from-a-cluster-node"></a>从群集节点运行清单时出现错误 "找不到 Dll"

当尝试使用存储迁移服务运行清单并针对 Windows Server 故障转移群集时，将收到以下错误：

```
DLL not found
[Error] Failed device discovery stage VolumeInfo with error: (0x80131524) Unable to load DLL 'Microsoft.FailoverClusters.FrameworkSupport.dll': The specified module could not be found. (Exception from HRESULT: 0x8007007E)
```

若要解决此问题，请在运行存储迁移服务 orchestrator 的服务器上安装 "故障转移群集管理工具" (RSAT 群集管理) 。

## <a name="error-there-are-no-more-endpoints-available-from-the-endpoint-mapper-when-running-inventory-against-a-windows-server-2003-source-computer"></a>针对 Windows Server 2003 源计算机运行清单时出现错误 "终结点映射器中没有更多的终结点可用"

尝试对 Windows Server 2003 源计算机使用存储迁移服务 orchestrator 运行清单时，会收到以下错误：

```
There are no more endpoints available from the endpoint mapper
```

此问题由 [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) 更新程序解决。

## <a name="uninstalling-a-cumulative-update-prevents-storage-migration-service-from-starting"></a>卸载累积更新会阻止存储迁移服务启动

卸载 Windows Server 累积更新可能会使存储迁移服务无法启动。 若要解决此问题，可以备份和删除存储迁移服务数据库：

1. 打开提升的 cmd 提示符，你是存储迁移服务协调器服务器上的管理员成员，然后运行：

     ```DOS
     TAKEOWN /d y /a /r /f c:\ProgramData\Microsoft\StorageMigrationService

     MD c:\ProgramData\Microsoft\StorageMigrationService\backup

     ICACLS c:\ProgramData\Microsoft\StorageMigrationService\* /grant Administrators:(GA)

     XCOPY c:\ProgramData\Microsoft\StorageMigrationService\* .\backup\*

     DEL c:\ProgramData\Microsoft\StorageMigrationService\* /q

     ICACLS c:\ProgramData\Microsoft\StorageMigrationService  /GRANT networkservice:F /T /C

     ICACLS c:\ProgramData\Microsoft\StorageMigrationService /GRANT networkservice:(GA) /T /C
     ```

2. 启动存储迁移服务服务，该服务将创建一个新数据库。

## <a name="error-clusctl_resource_netname_repair_vco-failed-against-netname-resource-and-windows-server-2008-r2-cluster-cutover-fails"></a>错误 "针对网络名称资源 CLUSCTL_RESOURCE_NETNAME_REPAIR_VCO 失败"，Windows Server 2008 R2 群集切换失败

当尝试对 Windows Server 2008 R2 群集源运行 cut 时，该剪切卡会停滞在 "重命名源计算机 ..." 阶段你会收到以下错误：

```
Log Name:      Microsoft-Windows-StorageMigrationService-Proxy/Debug
Source:        Microsoft-Windows-StorageMigrationService-Proxy
Date:          10/17/2019 6:44:48 PM
Event ID:      10000
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      WIN-RNS0D0PMPJH.contoso.com
Description:
10/17/2019-18:44:48.727 [Erro] Exception error: 0x1. Message: Control code CLUSCTL_RESOURCE_NETNAME_REPAIR_VCO failed against netName resource 2008r2FS., stackTrace:    at Microsoft.FailoverClusters.Framework.ClusterUtils.NetnameRepairVCO(SafeClusterResourceHandle netNameResourceHandle, String netName)
at Microsoft.FailoverClusters.Framework.ClusterUtils.RenameFSNetName(SafeClusterHandle ClusterHandle, String clusterName, String FsResourceId, String NetNameResourceId, String newDnsName, CancellationToken ct)
at Microsoft.StorageMigration.Proxy.Cutover.CutoverUtils.RenameFSNetName(NetworkCredential networkCredential, Boolean isLocal, String clusterName, String fsResourceId, String nnResourceId, String newDnsName, CancellationToken ct)    [d:\os\src\base\dms\proxy\cutover\cutoverproxy\CutoverUtils.cs::RenameFSNetName::1510]
```

此问题是由较早版本的 Windows Server 中缺少的 API 导致的。 目前没有办法迁移 Windows Server 2008 和 Windows Server 2003 群集。 你可以在 Windows Server 2008 R2 群集上执行清单和传输，然后手动更改群集的源文件服务器资源网络名称和 IP 地址，然后更改目标群集的网络名称和 IP 地址以匹配原始源，从而手动执行转换。

## <a name="cutover-hangs-on-38-mapping-network-interfaces-on-the-source-computer-when-using-static-ips"></a>在源计算机上的 "38% 映射网络接口" 上切换挂起使用静态 Ip 时

当尝试在源计算机上运行 cut 时，将源计算机设置为在一个或多个网络接口上使用新的静态 (不是 DHCP) IP 地址时，剪切的会停滞在源计算机上的 "38% 映射网络接口"。在存储迁移服务事件日志中收到以下错误：

```
Log Name:      Microsoft-Windows-StorageMigrationService-Proxy/Admin
Source:        Microsoft-Windows-StorageMigrationService-Proxy
Date:          11/13/2019 3:47:06 PM
Event ID:      20494
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      orc2019-rtm.corp.contoso.com
Description:
Couldn't set the IP address on the network adapter.

Computer: fs12.corp.contoso.com
Adapter: microsoft hyper-v network adapter
IP address: 10.0.0.99
Network mask: 16
Error: 40970
Error Message: Unknown error (0xa00a)

Guidance: Confirm that the Netlogon service on the computer is reachable through RPC and that the credentials provided are correct.
```

检查源计算机时，会显示原始 IP 地址无法更改。

如果在 Windows 管理中心的 "配置切换" 屏幕上选择了 "使用 DHCP"，则不会出现此问题，这种情况仅在指定新的静态 IP 地址时才会发生。

此问题有两种解决方案：

1. 此问题已由 [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) 更新首次解决。 之前的代码缺陷阻止了静态 IP 地址的所有使用。

2. 如果未在源计算机的网络接口上指定默认网关 IP 地址，则即使使用 KB4537818 更新也会出现此问题。 若要解决此问题，请在网络接口上使用 ( # A0) 或 New-netroute Powershell cmdlet 设置有效的默认 IP 地址。

## <a name="slower-than-expected-re-transfer-performance"></a>比预期重新传输性能慢

完成传输后，运行相同数据的后续重新传输后，即使源服务器上存在很少的数据发生更改，传输时间也不会显著提高。

当传输大量文件和嵌套文件夹时，这是预期的行为。 数据的大小不相关。 首先，我们在 [KB4512534](https://support.microsoft.com/help/4512534/windows-10-update-kb4512534) 中改进了此行为，并继续优化传输性能。 若要进一步调整性能，请查看 [优化清单和传输性能](https://docs.microsoft.com/windows-server/storage/storage-migration-service/faq#optimizing-inventory-and-transfer-performance)。

## <a name="data-does-not-transfer-user-renamed-when-migrating-to-or-from-a-domain-controller"></a>数据不会传输，用户在迁移到域控制器或从域控制器中进行重命名

从或向域控制器开始传输后：

 1. 不迁移数据，也不会在目标上创建任何共享。
 2. Windows 管理中心中显示了红色错误符号，无错误消息
 3. 一个或多个 AD 用户和域本地组已更改其名称和/或 Windows 2000 以前的登录属性

 4. 在存储迁移服务协调器上看到事件3509：

    ```
    Log Name:      Microsoft-Windows-StorageMigrationService/Admin
    Source:        Microsoft-Windows-StorageMigrationService
    Date:          1/10/2020 2:53:48 PM
    Event ID:      3509
    Task Category: None
    Level:         Error
    Keywords:
    User:          NETWORK SERVICE
    Computer:      orc2019-rtm.corp.contoso.com
    Description:
    Couldn't transfer storage for a computer.

    Job: dctest3
    Computer: dc02-2019.corp.contoso.com
    Destination Computer: dc03-2019.corp.contoso.com
    State: Failed
    Error: 53251
    Error Message: Local accounts migration failed with error System.Exception: -2147467259
        at Microsoft.StorageMigration.Service.DeviceHelper.MigrateSecurity(IDeviceRecord sourceDeviceRecord, IDeviceRecord destinationDeviceRecord, TransferConfiguration config, Guid proxyId, CancellationToken cancelToken)
    ```

    如果尝试使用存储迁移服务从或迁移到域控制器，并且使用 "迁移用户和组" 选项重命名或重新使用帐户，则这是预期的行为。 而不是选择 "不传输用户和组"。 [存储迁移服务不支持](faq.md)DC 迁移。 由于 DC 不具备真正的本地用户和组，因此存储迁移服务将这些安全主体视为在两个成员服务器之间迁移时的处理方式，并尝试根据指示的错误和损坏或复制的帐户调整 Acl。

如果你已经运行了一次或多次传输：

 1. 对 DC 使用以下 AD PowerShell 命令来查找任何已修改的用户或组 (更改 SearchBase 以匹配域可分辨名称) ：

    ```PowerShell
    Get-ADObject -Filter 'Description -like "*storage migration service renamed*"' -SearchBase 'DC=<domain>,DC=<TLD>' | ft name,distinguishedname
    ```

 2. 对于使用其原始名称返回的任何用户，请编辑其 "用户登录名 (Windows 2000) 之前，以删除存储迁移服务添加的随机字符后缀，以便此用户可以登录。

 3. 对于使用其原始名称返回的任何组，请将其 "组名 (Windows 2000) " 添加为删除存储迁移服务添加的随机字符后缀。

 4. 对于其名称现在包含存储迁移服务添加的后缀的任何已禁用的用户或组，你可以删除这些帐户。 你可以确认以后是否添加了用户帐户，因为它们只包含域用户组，并且将创建与存储迁移服务传输开始时间匹配的日期/时间。

    如果要将存储迁移服务用于域控制器以进行传输，请确保始终在 Windows 管理中心的 "传输设置" 页上选择 "不传输用户和组"。

## <a name="error-53-failed-to-inventory-all-specified-devices-when-running-inventory"></a>运行清单时出现错误53，"未能清点所有指定的设备"

尝试运行清单时，会收到：

```
Failed to inventory all specified devices

Log Name:      Microsoft-Windows-StorageMigrationService/Admin
Source:        Microsoft-Windows-StorageMigrationService
Date:          1/16/2020 8:31:17 AM
Event ID:      2516
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      ned.corp.contoso.com
Description:
Couldn't inventory files on the specified endpoint.
Job: ned1
Computer: ned.corp.contoso.com
Endpoint: hithere
State: Failed
File Count: 0
File Size in KB: 0
Error: 53
Error Message: Endpoint scan failed
Guidance: Check the detailed error and make sure the inventory requirements are met. This could be because of missing permissions on the source computer.

Log Name:      Microsoft-Windows-StorageMigrationService-Proxy/Debug
Source:        Microsoft-Windows-StorageMigrationService-Proxy
Date:          1/16/2020 8:31:17 AM
Event ID:      10004
Task Category: None
Level:         Critical
Keywords:
User:          NETWORK SERVICE
Computer:      ned.corp.contoso.com
Description:
01/16/2020-08:31:17.031 [Crit] Consumer Task failed with error:The network path was not found.
. StackTrace=   at Microsoft.Win32.RegistryKey.Win32ErrorStatic(Int32 errorCode, String str)
    at Microsoft.Win32.RegistryKey.OpenRemoteBaseKey(RegistryHive hKey, String machineName, RegistryView view)
    at Microsoft.StorageMigration.Proxy.Service.Transfer.FileDirUtils.GetEnvironmentPathFolders(String ServerName, Boolean IsServerLocal)
    at Microsoft.StorageMigration.Proxy.Service.Discovery.ScanUtils.<ScanSMBEndpoint>d__3.MoveNext()
    at Microsoft.StorageMigration.Proxy.EndpointScanOperation.Run()
    at Microsoft.StorageMigration.Proxy.Service.Discovery.EndpointScanRequestHandler.ProcessRequest(EndpointScanRequest scanRequest, Guid operationId)
    at Microsoft.StorageMigration.Proxy.Service.Discovery.EndpointScanRequestHandler.ProcessRequest(Object request)
    at Microsoft.StorageMigration.Proxy.Common.ProducerConsumerManager`3.Consume(CancellationToken token)

01/16/2020-08:31:10.015 [Erro] Endpoint Scan failed. Error: (53) The network path was not found.
Stack trace:
    at Microsoft.Win32.RegistryKey.Win32ErrorStatic(Int32 errorCode, String str)
    at Microsoft.Win32.RegistryKey.OpenRemoteBaseKey(RegistryHive hKey, String machineName, RegistryView view)
```

在此阶段，存储迁移服务协调器正在尝试执行远程注册表读取，以确定源计算机配置，但源服务器会拒绝该注册表路径不存在的情况。 这可能是由于：

 - 远程注册表服务未在源计算机上运行。
 - 防火墙不允许从 Orchestrator 远程连接到源服务器。
 - 源迁移帐户没有连接到源计算机的远程注册表权限。
 - 源迁移帐户没有源计算机注册表中的读取权限，在 "HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion" 或 "HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\LanmanServer" 下

## <a name="cutover-hangs-on-38-mapping-network-interfaces-on-the-source-computer"></a>在源计算机上的 "38% 映射网络接口" 上切换挂起

当尝试对源计算机运行 cut 时，剪切的会停滞在源计算机上的 "38% 映射网络接口" 阶段。在存储迁移服务事件日志中收到以下错误：

```
Log Name:      Microsoft-Windows-StorageMigrationService-Proxy/Admin
Source:        Microsoft-Windows-StorageMigrationService-Proxy
Date:          1/11/2020 8:51:14 AM
Event ID:      20505
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      nedwardo.contosocom
Description:
Couldn't establish a CIM session with the computer.

Computer: 172.16.10.37
User Name: nedwardo\MsftSmsStorMigratSvc
Error: 40970
Error Message: Unknown error (0xa00a)

Guidance: Confirm that the Netlogon service on the computer is reachable through RPC and that the credentials provided are correct.
```

此问题的原因是组策略在源计算机上设置以下注册表值： "HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\LocalAccountTokenFilterPolicy = 0"

此设置不是标准组策略的一部分，它是使用 [Microsoft 安全符合性工具包](https://www.microsoft.com/download/details.aspx?id=55319)配置的加载项：

- Windows Server 2012 R2： "计算机配置 \ 管理 Templates\SCM：将哈希 Mitigations\Apply UAC 限制传递到网络登录上的本地帐户"

- 孤行服务器2016： "计算机配置 \ 管理 Templates\MS Security Guide\Apply 对网络登录上的本地帐户的 UAC 限制"

还可以使用组策略首选项设置自定义注册表设置。 您可以使用 GPRESULT 工具来确定将此设置应用于源计算机的策略。

存储迁移服务暂时将 [LocalAccountTokenFilterPolicy](https://support.microsoft.com/help/951016/description-of-user-account-control-and-remote-restrictions-in-windows) 启用为整个过程的一部分，并在完成后将其删除。 如果组策略将组策略对象 (GPO) ，则会替代存储迁移服务，并阻止剪切。

若要解决此问题，请使用以下选项之一：

1. 临时从应用此冲突的 GPO 的 Active Directory OU 中移动源计算机。
2. 临时禁用应用此冲突策略的 GPO。
3. 临时创建一个新的 GPO，该 GPO 将此设置设置为 "已禁用"，并应用于源服务器的特定 OU，其优先级高于任何其他 Gpo。

## <a name="inventory-or-transfer-fail-when-using-credentials-from-a-different-domain"></a>使用不同域中的凭据时清点或传输失败

当尝试使用存储迁移服务运行清单或传输，并在使用从目标服务器以外的其他域中迁移凭据的情况下，将 Windows Server 定向到该服务时，会收到以下错误
```
Exception from HRESULT:0x80131505

The server was unable to process the request due to an internal error

04/28/2020-11:31:01.169 [Error] Failed device discovery stage SystemInfo with error: (0x490) Could not find computer object 'myserver' in Active Directory    [d:\os\src\base\dms\proxy\discovery\discoveryproxy\DeviceDiscoveryOperation.cs::TryStage::1042]
```

再次检查日志显示，迁移帐户和迁移的服务器在不同的域中进行迁移，或者两者位于不同的域中：

```
06/25/2020-10:11:16.543 [Info] Creating new job=NedJob user=**CONTOSO**\ned
[d:\os\src\base\dms\service\StorageMigrationService.IInventory.cs::CreateJob::133]
```

```
GetOsVersion(fileserver75.**corp**.contoso.com)    [d:\os\src\base\dms\proxy\common\proxycommon\CimSessionHelper.cs::GetOsVersion::66] 06/25/2020-10:20:45.368 [Info] Computer 'fileserver75.corp.contoso.com': OS version
```

此问题是由存储迁移服务中的代码缺陷导致的。 若要解决此问题，请使用源计算机和目标计算机所属的域中的迁移凭据。 例如，如果源计算机和目标计算机属于 "contoso.com" 林中的 "corp.contoso.com" 域，请使用 "corp\myaccount" 执行迁移，而不是 "contoso\myaccount" 凭据。

## <a name="inventory-fails-with-element-not-found"></a>清点失败，出现 "找不到元素"

请参考以下方案：

你的源服务器具有 DNS 主机名并且 Active Directory 名称超过15个 unicode 字符，如 "iamaverylongcomputername"。 按照设计，Windows 不允许将旧的 NetBIOS 名称设置为长时间设置并在服务器名为的情况下发出警告，因为 NetBIOS 名称将被截断为15个 unicode 宽字符 (例如： "iamaverylongcom" ) 。 当你尝试清点此计算机时，将在 Windows 管理中心和事件日志中收到：

```DOS
"Element not found"
========================

Log Name:      Microsoft-Windows-StorageMigrationService/Admin
Source:        Microsoft-Windows-StorageMigrationService
Date:          4/10/2020 10:49:19 AM
Event ID:      2509
Task Category: None
Level:         Error
Keywords:
User:          NETWORK SERVICE
Computer:      WIN-6PJAG3DHPLF.corp.contoso.com
Description:
Couldn't inventory a computer.

Job: longnametest
Computer: iamaverylongcomputername.corp.contoso.com
State: Failed
Error: 1168
Error Message:

Guidance: Check the detailed error and make sure the inventory requirements are met. The inventory couldn't determine any aspects of the specified source computer. This could be because of missing permissions or privileges on the source or a blocked firewall port.
```

此问题是由存储迁移服务中的代码缺陷导致的。 唯一的解决方法是将计算机重命名为具有与 NetBIOS 名称相同的名称，然后使用 [NETDOM COMPUTERNAME/add](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc835082(v=ws.11)) 来添加一个备用计算机名称，其中包含在开始清点之前使用的较长名称。 存储迁移服务支持迁移备用计算机名称。

## <a name="see-also"></a>另请参阅

- [存储迁移服务概述](overview.md)
