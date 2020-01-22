---
ms.date: 09/27/2018
ms.topic: conceptual
keywords: OpenSSH, SSH, SSHD, 安装, 设置
contributor: maertendMSFT
ms.product: w10
author: maertendMSFT
title: 适用于 Windows 的 OpenSSH 服务器配置
ms.openlocfilehash: 5eb3d86950d169fd01512d330f0c04669beeffae
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259042"
---
# <a name="openssh-server-configuration-for-windows-10-1809-and-server-2019"></a>适用于 Windows 10 1809 和 Server 2019 的 OpenSSH 服务器配置

本主题介绍了适用于 OpenSSH 服务器 (sshd) 的特定于 Windows 的配置。 

OpenSSH 在 [OpenSSH.com](https://www.openssh.com/manual.html) 上在线维护有关配置选项的详细文档，本文档集中没有重述。 

## <a name="configuring-the-default-shell-for-openssh-in-windows"></a>为 Windows 中的 OpenSSH 配置默认 shell

默认命令 shell 提供用户使用 SSH 连接到服务器时看到的体验。 初始默认 Windows 是 Windows Command shell (cmd.exe)。 Windows 还包括了 PowerShell 和 Bash，第三方命令 shell 也可用于 Windows，并可配置为服务器的默认 shell。

若要设置默认命令 shell，请首先确认 OpenSSH 安装文件夹是否位于系统路径上。 对于 Windows，默认安装文件夹为 SystemDrive:WindowsDirectory\System32\openssh。 以下命令显示当前路径设置，并向其中添加默认的 OpenSSH 安装文件夹。 

命令 shell | 要使用的命令
------------- | -------------- 
命令 | path
PowerShell | $env:path

通过将 shell 可执行文件的完整路径添加到 \SOFTWARE\OpenSSH 字符串值 DefaultShell 中的 Computer\HKEY_LOCAL_MACHINE\SOFTWARE\OpenSSH，在 Windows 注册表中配置默认 ssh shell。 

例如，以下 Powershell 命令将默认 shell 设置为 PowerShell.exe：

```powershell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```

## <a name="windows-configurations-in-sshd_config"></a>Sshd_config 中的 Windows 配置 

在 Windows 中，sshd 默认情况下从 %programdata%\ssh\sshd_config 中读取配置数据，也可以通过使用 -f 参数启动 sshd 来指定不同的配置文件。
如果该文件不存在，则在启动该服务时，sshd 将使用默认配置生成一个文件。

下面列出的元素提供了通过 sshd_config 中的条目可以实现的特定于 Windows 的配置。 可以在其中实现的其他一些配置设置在此处没有列出，因为在线 [Win32 OpenSSH 文档](https://github.com/powershell/win32-openssh/wiki)中详细介绍了它们。 


### <a name="allowgroups-allowusers-denygroups-denyusers"></a>AllowGroups、AllowUsers、DenyGroups、DenyUsers 

使用 AllowGroups、AllowUsers、DenyGroups 和 DenyUsers 指令控制哪些用户和组可以连接到服务器。 allow/deny 指令按以下顺序处理：DenyUsers、AllowUsers、DenyGroups，最后是 AllowGroups。 必须以小写形式指定所有帐户名称。 有关通配符模式的详细信息，请参阅 ssh_config 中的 PATTERNS。

当使用域用户或组配置基于用户/组的规则时，请使用以下格式：``` user?domain* ```。
Windows 允许使用多种格式来指定域主体，但许多格式与标准 Linux 模式冲突。 因此，添加了 * 来涵盖 FQDN。 此外，此方法使用了 "?"（而非 @）来避免与 username@host 格式发生冲突。 

工作组用户/组和连接到 internet 的帐户始终解析为其本地帐户名称（不包括域部分，类似于标准 Unix 名称）。 域用户和组严格解析为 [NameSamCompatible](https://docs.microsoft.com/windows/desktop/api/secext/ne-secext-extended_name_format) 格式 - domain_short_name\user_name。 所有基于用户/组的配置规则都需要遵循此格式。

域用户和组的示例 

```
DenyUsers contoso\admin@192.168.2.23 : blocks contoso\admin from 192.168.2.23
DenyUsers contoso\* : blocks all users from contoso domain
AllowGroups contoso\sshusers : only allow users from contoso\sshusers group
```

本地用户和组的示例 

```
AllowUsers localuser@192.168.2.23
AllowGroups sshusers
```

### <a name="authenticationmethods"></a>AuthenticationMethods 

对于 Windows OpenSSH，唯一可用的身份验证方法是“password”和“publickey”。

### <a name="authorizedkeysfile"></a>AuthorizedKeysFile 

默认值为“.ssh/authorized_keys .ssh/authorized_keys2”。 如果路径不是绝对路径，则它相对于用户的主目录（或配置文件图像路径）。 示例： c:\users\user。

### <a name="chrootdirectory-support-added-in-v7700"></a>ChrootDirectory（在 v7.7.0.0 中添加的支持）

此指令仅在 sftp 会话中受支持。 到 cmd.exe 的远程会话不遵循此规则。 若要设置仅限 sftp 的 chroot 服务器，请将 ForceCommand 设置为 internal-sftp。 还可以通过实现仅允许 scp 和 sftp 的自定义 shell，来通过 chroot 设置 scp。

### <a name="hostkey"></a>HostKey

默认值为 %programdata%/ssh/ssh_host_ecdsa_key、%programdata%/ssh/ssh_host_ed25519_key、%programdata%/ssh/ssh_host_dsa_key 和 %programdata%/ssh/ssh_host_rsa_key。 如果默认值不存在，则 sshd 会在服务启动时自动生成这些值。

### <a name="match"></a>匹配

请注意此部分中的模式规则。 用户和组名称应采用小写。

### <a name="permitrootlogin"></a>PermitRootLogin

在 Windows 中不适用。 若要阻止管理员登录，请将 Administrators 与 DenyGroups 指令一起使用。

### <a name="syslogfacility"></a>SyslogFacility

如果需要基于文件的日志记录，请使用 LOCAL0。 日志将在 %programdata%\ssh\logs 下生成。
任何其他值（包括默认值 AUTH）都会将日志记录定向到 ETW。 有关详细信息，请参阅 Windows 中的日志记录功能。

### <a name="not-supported"></a>不支持 

Windows Server 2019 和 Windows 10 1809 中附带的 OpenSSH 版本中未提供以下配置选项：

* AcceptEnv
* AllowStreamLocalForwarding
* AuthorizedKeysCommand
* AuthorizedKeysCommandUser
* AuthorizedPrincipalsCommand
* AuthorizedPrincipalsCommandUser
* 压缩
* ExposeAuthInfo
* GSSAPIAuthentication
* GSSAPICleanupCredentials
* GSSAPIStrictAcceptorCheck
* HostbasedAcceptedKeyTypes
* HostbasedAuthentication
* HostbasedUsesNameFromPacketOnly
* IgnoreRhosts
* IgnoreUserKnownHosts
* KbdInteractiveAuthentication
* KerberosAuthentication
* KerberosGetAFSToken
* KerberosOrLocalPasswd
* KerberosTicketCleanup
* PermitTunnel
* PermitUserEnvironment
* PermitUserRC
* PidFile
* PrintLastLog
* RDomain
* StreamLocalBindMask
* StreamLocalBindUnlink
* StrictModes
* X11DisplayOffset
* X11Forwarding
* X11UseLocalhost
* XAuthLocation

