---
title: 如何在 Windows 中检测、启用和禁用 SMBv1、SMBv2 和 SMBv3
description: 介绍如何启用和禁用 Windows 客户端和服务器环境中的服务器消息块协议 (SMBv1、SMBv2 和 SMBv3) 。
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: f96302242eca58d589586fa44e6e7cd04ef98cc1
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083638"
---
# <a name="how-to-detect-enable-and-disable-smbv1-smbv2-and-smbv3-in-windows"></a>如何在 Windows 中检测、启用和禁用 SMBv1、SMBv2 和 SMBv3

## <a name="summary"></a>总结

本文介绍如何在 SMB 客户端和服务器组件上启用和禁用 (SMB) 版本 1 (SMBv1) 、SMB 版本 2 (SMBv2) 和 SMB 版本 3 (SMBv3) 的服务器消息块。 

> [!IMPORTANT]
> 建议 **你不要禁用 SMBv2** 或 SMBv3。 仅将 SMBv2 或 SMBv3 作为临时故障排除度量值禁用。 不要让 SMBv2 或 SMBv3 处于禁用状态。  

在 Windows 7 和 Windows Server 2008 R2 中，禁用 SMBv2 将停用以下功能： 
 
- 请求复合-允许将多个 SMB 2 请求作为单个网络请求发送    
- 更大的读写，更好地使用更快的网络    
- 文件夹和文件属性的缓存-客户端保留文件夹和文件的本地副本    
- 持久句柄-如果有临时断开连接，则允许连接以透明方式重新连接到服务器    
- 改进的消息签名-HMAC SHA-256 将 MD5 替换为哈希算法    
- 文件共享的可伸缩性改进-每个服务器的用户、共享和打开文件的数量大大增加    
- 支持符号链接    
- 客户端 oplock 租赁模式-限制在客户端与服务器之间传输的数据，提高高延迟网络的性能并提高 SMB 服务器的可伸缩性    
- 大 MTU 支持-完全使用 10-gigabye (GB) 以太网    
- 提高了能效-已向服务器打开文件的客户端可以进入睡眠状态    

在 Windows 8、Windows 8.1、Windows 10、Windows Server 2012、Windows Server 2012 R2、Windows Server 2016 和 Windows Server 2019 中，禁用 SMBv3 将停用以下功能 (以及) 前面的列表中所述的 SMBv2 功能： 
 
- 透明故障转移-客户端在维护或故障转移过程中重新连接而不中断群集节点    
- Scale Out –对所有文件群集节点上的共享数据进行并发访问     
- 多通道-如果客户端和服务器之间有多个路径，则聚合网络带宽和容错  
- SMB Direct –为非常高的性能增加了 RDMA 网络支持，并提供低延迟和低 CPU 使用率    
- 加密–提供端对端加密并防止在不受信任的网络上窃听    
- 目录租用-通过缓存改善分支机构中的应用程序响应时间    
- 性能优化-优化小型随机读/写 i/o

##  <a name="more-information"></a>更多信息

Windows Vista 和 Windows Server 2008 中引入了 SMBv2 协议。

Windows 8 和 Windows Server 2012 中引入了 SMBv3 协议。

有关 SMBv2 和 SMBv3 功能的功能的详细信息，请参阅以下文章：

[服务器消息块概述](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831795(v=ws.11))

[SMB 中的新增功能](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff625695(v=ws.10))  

## <a name="how-to-gracefully-remove-smb-v1-in-windows-81-windows-10-windows-2012-r2-windows-server-2016-and-windows-server-2019"></a>如何在 Windows 8.1、Windows 10、Windows 2012 R2、Windows Server 2016 和 Windows Server 2019 中正常删除 SMB v1

#### <a name="powershell-methods"></a>PowerShell 方法

##### <a name="smb-v1-client-and-server"></a>SMB v1 (客户端和服务器) 

- 察觉 

  ```PowerShell
  Get-WindowsOptionalFeature -Online -FeatureName smb1protocol
  ```

- 禁用 

  ```PowerShell
  Disable-WindowsOptionalFeature -Online -FeatureName smb1protocol
  ```

- 启用： 

  ```PowerShell
  Enable-WindowsOptionalFeature -Online -FeatureName smb1protocol
  ```

#### <a name="windows-server-2012-r2-windows-server-2016-windows-server-2019-server-manager-method-for-disabling-smb"></a>Windows Server 2012 R2、Windows Server 2016、Windows Server 2019：用于禁用 SMB 的服务器管理器方法

##### <a name="smb-v1"></a>SMB v1

![服务器管理器-仪表板方法](media/detect-enable-and-disable-smbv1-v2-v3-1.png)

#### <a name="windows-81-and-windows-10-powershell-method"></a>Windows 8.1 和 Windows 10： PowerShell 方法

##### <a name="smb-v1-protocol"></a>SMB v1 协议

- 察觉 
  
  ```PowerShell
  Get-WindowsOptionalFeature –Online –FeatureName SMB1Protocol
  ```

- 禁用 

  ```PowerShell
  Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
  ```

- 启用： 

  ```PowerShell
  Enable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
  ```

##### <a name="smb-v2v3protocol-only-disables-smb-v2v3-server"></a>SMB v2/v3 协议 (仅禁用 SMB v2/v3 服务器) 

- 察觉 
  
  ```PowerShell
  Get-SmbServerConfiguration | Select EnableSMB2Protocol
  ```

- 禁用 
  
  ```PowerShell
  Set-SmbServerConfiguration –EnableSMB2Protocol $false
  ```

- 启用：

  ```PowerShell
  Set-SmbServerConfiguration –EnableSMB2Protocol $true
  ```

#### <a name="windows-81-and-windows-10-add-or-remove-programs-method"></a>Windows 8.1 和 Windows 10：添加或删除程序方法

![添加/删除程序客户端方法](media/detect-enable-and-disable-smbv1-v2-v3-2.png)

## <a name="how-to-detect-status-enable-and-disable-smb-protocols-on-the-smb-server"></a>如何在 SMB 服务器上检测状态、启用和禁用 SMB 协议

### <a name="for-windows-8-and-windows-server-2012"></a>适用于 Windows 8 和 Windows Server 2012

Windows 8 和 Windows Server 2012 引入了新的 **SMBServerConfiguration** Windows PowerShell cmdlet。 Cmdlet 可用于启用或禁用服务器组件上的 SMBv1、SMBv2 和 SMBv3 协议。  

> [!NOTE]   
> 启用或禁用 Windows 8 或 Windows Server 2012 中的 SMBv2 时，也会启用或禁用 SMBv3。 之所以发生此行为，是因为这些协议共享同一堆栈。     

运行 **SMBServerConfiguration** cmdlet 后，无需重新启动计算机。 

##### <a name="smb-v1-on-smb-server"></a>SMB 服务器上的 SMB v1

- 察觉 
  
  ```PowerShell
  Get-SmbServerConfiguration | Select EnableSMB1Protocol
  ```

- 禁用 

  ```PowerShell
  Set-SmbServerConfiguration -EnableSMB1Protocol $false
  ```

- 启用： 
  ```PowerShell
  Set-SmbServerConfiguration -EnableSMB1Protocol $true
  ```

有关详细信息，请参阅 [Microsoft 服务器存储](https://techcommunity.microsoft.com/t5/Storage-at-Microsoft/Stop-using-SMB1/ba-p/425858)。 
##### <a name="smb-v2v3-on-smb-server"></a>Smb 服务器上的 SMB v2/v3

- 察觉

  ```PowerShell
  Get-SmbServerConfiguration | Select EnableSMB2Protocol
  ```

- 禁用 
  
  ```PowerShell
  Set-SmbServerConfiguration -EnableSMB2Protocol $false
  ```

- 启用：
  
  ```PowerShell
  Set-SmbServerConfiguration -EnableSMB2Protocol $true
  ```

### <a name="for-windows-7-windows-server-2008-r2-windows-vista-and-windows-server-2008"></a>适用于 Windows 7、Windows Server 2008 R2、Windows Vista 和 Windows Server 2008

若要在运行 Windows 7、Windows Server 2008 R2、Windows Vista 或 Windows Server 2008 的 SMB 服务器上启用或禁用 SMB 协议，请使用 Windows PowerShell 或注册表编辑器。 

#### <a name="powershell-methods"></a>PowerShell 方法

> [!NOTE]
> 此方法需要 PowerShell 2.0 或更高版本的 PowerShell。

##### <a name="smb-v1-on-smb-server"></a>SMB 服务器上的 SMB v1

察觉

```PowerShell
Get-Item HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters | ForEach-Object {Get-ItemProperty $_.pspath}
```

默认配置 = Enabled (未) 创建注册表项，因此不会返回 SMB1 值

禁用

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB1 -Type DWORD -Value 0 –Force
```

启用：  

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB1 -Type DWORD -Value 1 –Force
```  

**注意** 进行这些更改之后，必须重新启动计算机。 有关详细信息，请参阅 [Microsoft 服务器存储](https://techcommunity.microsoft.com/t5/storage-at-microsoft/stop-using-smb1/ba-p/425858)。 
##### <a name="smb-v2v3-on-smb-server"></a>Smb 服务器上的 SMB v2/v3

察觉  

```PowerShell
Get-ItemProperty HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters | ForEach-Object {Get-ItemProperty $_.pspath} 
```

禁用

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB2 -Type DWORD -Value 0 –Force  
```

启用：

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB2 -Type DWORD -Value 1 –Force 
```

> [!NOTE]
> 进行这些更改之后，必须重新启动计算机。 

#### <a name="registry-editor"></a>注册表编辑器

> [!IMPORTANT]
> 请认真遵循本部分所述的步骤。 如果注册表修改不正确，可能会发生严重问题。 在修改注册表之前，请[备份注册表](https://support.microsoft.com/help/322756)，以便在出现问题时可以还原。
 
若要在 SMB 服务器上启用或禁用 SMBv1，请配置以下注册表项：

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**

```
Registry entry: SMB1
REG_DWORD: 0 = Disabled
REG_DWORD: 1 = Enabled
Default: 1 = Enabled (No registry key is created)
```

若要在 SMB 服务器上启用或禁用 SMBv2，请配置以下注册表项： 

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**

```
Registry entry: SMB2
REG_DWORD: 0 = Disabled
REG_DWORD: 1 = Enabled
Default: 1 = Enabled (No registry key is created) 
```

> [!NOTE]
> 进行这些更改之后，必须重新启动计算机。 

## <a name="how-to-detect-status-enable-and-disable-smb-protocols-on-the-smb-client"></a>如何在 SMB 客户端上检测状态、启用和禁用 SMB 协议

### <a name="for-windows-vista-windows-server-2008-windows-7-windows-server-2008-r2-windows-8-and-windows-server-2012"></a>对于 Windows Vista、Windows Server 2008、Windows 7、Windows Server 2008 R2、Windows 8 和 Windows Server 2012

> [!NOTE]
> 启用或禁用 Windows 8 或 Windows Server 2012 中的 SMBv2 时，也会启用或禁用 SMBv3。 之所以发生此行为，是因为这些协议共享同一堆栈。 

##### <a name="smb-v1-on-smb-client"></a>SMB v1 （在 SMB 客户端上）

- Detect
  
  ```cmd
  sc.exe qc lanmanworkstation
  ```

- 禁用
  
  ```cmd
  sc.exe config lanmanworkstation depend= bowser/mrxsmb20/nsi
  sc.exe config mrxsmb10 start= disabled
  ```

- 启用：

  ```cmd
  sc.exe config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi
  sc.exe config mrxsmb10 start= auto
  ```

有关详细信息，请参阅 [Microsoft 的服务器存储](https://techcommunity.microsoft.com/t5/storage-at-microsoft/stop-using-smb1/ba-p/425858) 
##### <a name="smb-v2v3-on-smb-client"></a>Smb v2/在 SMB 客户端上

- 察觉

  ```cmd
  sc.exe qc lanmanworkstation
  ```

- 禁用

  ```cmd
  sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi
  sc.exe config mrxsmb20 start= disabled 
  ```

- 启用：

  ```cmd
  sc.exe config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi
  sc.exe config mrxsmb20 start= auto
  ```

> [!NOTE]
> - 你必须在提升的命令提示符下运行这些命令。    
> - 进行这些更改之后，必须重新启动计算机。    
 

## <a name="disable-smbv1-server-with-group-policy"></a>通过组策略禁用 SMBv1 服务器

此过程在注册表中配置以下新项：

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters** 

- 注册表项： **SMB1** 
- REG_DWORD： **0** = 已禁用   

若要使用组策略进行配置，请执行以下步骤：
 
1. 打开“组策略管理控制台”****。 右键单击应该包含新首选项的组策略对象 (GPO)，然后单击 **“编辑”**。

2. 在控制台树中的 " **计算机配置**" 下，展开 " **首选项** " 文件夹，然后展开 " **Windows 设置** " 文件夹。

3. 右键单击 " **注册表** " 节点，指向 " **新建**"，然后选择 " **注册表项**"。

   ![注册表-New-Registry 项](media/detect-enable-and-disable-smbv1-v2-v3-3.png)    
 
在 " **新建注册表属性**" 对话框中，选择以下项： 
 
- **操作**：创建    
- **Hive**： HKEY_LOCAL_MACHINE    
- **密钥路径**： SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters    
- **值名称**： SMB1    
- **值类型**： REG_DWORD    
- **值数据**：0    
 
![新注册表属性-常规](media/detect-enable-and-disable-smbv1-v2-v3-4.png)

这将禁用 SMBv1 服务器组件。 此组策略必须应用于域中的所有必要工作站、服务器和域控制器。

> [!NOTE]
> [WMI 筛选器](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc947846(v=ws.10)) 还可以设置为排除不受支持的操作系统或所选的排除项，例如 Windows XP。

> [!IMPORTANT]
> 如果在不支持 SMBv2 或 SMBv3 的旧版 Windows XP 或更低版本的 Linux 和第三方系统 (不支持或) 的域控制器上进行这些更改，请务必小心。     

## <a name="disable-smbv1-client-with-group-policy"></a>通过组策略禁用 SMBv1 客户端

若要禁用 SMBv1 客户端，需要更新服务注册表项以禁用**MRxSMB10**的启动，然后需要从**LanmanWorkstation**条目中删除对**MRxSMB10**的依赖项，以便它能够正常启动，而无需首先启动**MRxSMB10** 。

这将更新并替换注册表中以下2项中的默认值： 

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\services\mrxsmb10** 

注册表项： **开始** REG_DWORD： **4**= 已禁用

**HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\LanmanWorkstation** 

注册表项： **DependOnService** REG_MULTI_SZ： **"Bowser"、"MRxSmb20"、"NSI"**   

> [!NOTE]
> 默认已包含的 MRxSMB10，现已删除为依赖项。

若要使用组策略进行配置，请执行以下步骤：
 
1. 打开“组策略管理控制台”****。 右键单击应该包含新首选项的组策略对象 (GPO)，然后单击 **“编辑”**。

2. 在控制台树中的 " **计算机配置**" 下，展开 " **首选项** " 文件夹，然后展开 " **Windows 设置** " 文件夹。

3. 右键单击 " **注册表** " 节点，指向 " **新建**"，然后选择 " **注册表项**"。    

4. 在 " **新建注册表属性** " 对话框中，选择以下项： 
 
   - **操作**：更新
   - **Hive**： HKEY_LOCAL_MACHINE
   - **密钥路径**： SYSTEM\CurrentControlSet\services\mrxsmb10
   - **值名称**： Start
   - **值类型**： REG_DWORD
   - **值数据**：4
 
   ![启动属性-常规](media/detect-enable-and-disable-smbv1-v2-v3-5.png)

5. 然后删除刚刚禁用的 **MRxSMB10** 的依赖项。

   在 " **新建注册表属性** " 对话框中，选择以下项： 
 
   - **操作**：替换
   - **Hive**： HKEY_LOCAL_MACHINE
   - **密钥路径**： SYSTEM\CurrentControlSet\Services\LanmanWorkstation
   - **值名称**： DependOnService
   - **值类型**： REG_MULTI_SZ 
   - **值数据**：
      - Bowser
      - MRxSmb20
      - NSI
 
   > [!NOTE]
   > 这三个字符串不会有项目符号 (请参阅以下屏幕截图) 。

   ![DependOnService 属性](media/detect-enable-and-disable-smbv1-v2-v3-6.png) 

   在许多版本的 Windows 中，默认值都包含 **MRxSMB10** ，因此通过使用此多值字符串替换它们，这实际上是将 **MRxSMB10** 删除为 **LanmanServer** 的依赖项，并从四个默认值向下转到上述三个值。

   > [!NOTE]
   > 使用组策略管理控制台时，不必使用引号或逗号。 只需在单独的行中键入每个条目。

6. 重新启动目标系统以完成 SMB v1 的禁用。

### <a name="summary"></a>总结

如果所有设置都在 (GPO) 相同的组策略对象中，组策略管理将显示以下设置。

![组策略管理编辑器注册表](media/detect-enable-and-disable-smbv1-v2-v3-7.png) 

### <a name="testing-and-validation"></a>测试和验证

配置这些配置后，允许对策略进行复制和更新。 如有必要，请在命令提示符下运行 **gpupdate/force** ，然后查看目标计算机以确保正确应用注册表设置。 请确保 SMB v2 和 SMB v3 在环境中的所有其他系统上正常工作。

> [!NOTE]
> 请勿忘记重新启动目标系统。
