---
title: manage-bde 保护程序
description: Manage-bde 保护程序命令的参考主题，用于管理用于 BitLocker 加密密钥的保护方法。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f9b22c5-cc93-45df-9165-bedee94998da
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/06/2018
ms.openlocfilehash: 999c92fd9f2bfedad92a9c68c1528ee66836f315
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222628"
---
# <a name="manage-bde-protectors"></a>manage-bde 保护程序

> 适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016

管理用于 BitLocker 加密密钥的保护方法。

## <a name="syntax"></a>语法

```
manage-bde -protectors [{-get|-add|-delete|-disable|-enable|-adbackup|-aadbackup}] <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ----------- | ----------- |
| -get | 显示在驱动器上启用的所有密钥保护方法，并提供其类型和标识符（ID）。 |
| -添加 | 添加使用额外 **-添加**参数指定的密钥保护方法。 |
| -delete | 删除 BitLocker 使用的密钥保护方法。 除非使用可选 **-delete**参数指定要删除的保护程序，否则将从驱动器中删除所有密钥保护程序。 删除驱动器上的最后一个保护程序时，将禁用驱动器的 BitLocker 保护，以确保不会无意中丢失对数据的访问权限。 |
| -disable | 禁用保护，使任何人都可以通过使加密密钥在驱动器上不受保护的加密密钥来访问加密的数据。 不会删除任何密钥保护程序。 将在下次启动 Windows 时恢复保护，除非使用可选**的-disable**参数指定重启计数。 |
| -enable | 通过从驱动器中删除不安全的加密密钥来启用保护。 将强制实施驱动器上的所有已配置的密钥保护程序。 |
| -adbackup | 备份指定的驱动器的所有恢复信息 Active Directory 域服务（AD DS）。 若要仅备份一个恢复密钥以便 AD DS，请附加 **-id**参数，并指定要备份的特定恢复密钥的 id。 |
| -aadbackup | 备份指定的驱动器的所有恢复信息 Azure Active Directory （Azure AD）。 若要仅备份一个恢复密钥以便 Azure AD，请附加 **-id**参数，并指定要备份的特定恢复密钥的 id。 |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -computername | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

#### <a name="additional--add-parameters"></a>附加参数

-Add 参数还可以使用这些有效的附加参数。

```
manage-bde -protectors -add [<drive>] [-forceupgrade] [-recoverypassword <numericalpassword>] [-recoverykey <pathtoexternalkeydirectory>]
[-startupkey <pathtoexternalkeydirectory>] [-certificate {-cf <pathtocertificatefile>|-ct <certificatethumbprint>}] [-tpm] [-tpmandpin]
[-tpmandstartupkey <pathtoexternalkeydirectory>] [-tpmandpinandstartupkey <pathtoexternalkeydirectory>] [-password][-adaccountorgroup <securityidentifier> [-computername <name>]
[{-?|/?}] [{-help|-h}]
```

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -ms-fve-recoverypassword | 添加数字密码保护程序。 你还可以使用 **-rp**作为此命令的缩写形式。 |
| `<numericalpassword>` | 表示恢复密码。 |
| -recoverykey | 添加用于恢复的外部密钥保护程序。 你还可以使用 **-rk**作为此命令的缩写形式。 |
| `<pathtoexternalkeydirectory>` | 表示恢复密钥的目录路径。 |
| -启动 | 添加用于启动的外部密钥保护程序。 你还可以使用 **-sk**作为此命令的缩写形式。 |
| `<pathtoexternalkeydirectory>` | 表示启动密钥的目录路径。 |
| -证书 | 为数据驱动器添加公钥保护程序。 你还可以使用 **-cert**作为此命令的缩写形式。 |
| -cf | 指定将用于提供公钥证书的证书文件。 |
| <pathtocertificatefile> | 表示证书文件的目录路径。 |
| -ct | 指定将使用证书指纹来标识公钥证书 |
| `<certificatethumbprint>` | 指定要使用的证书的指纹属性的值。 例如，对于 a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b 的证书指纹值，应将其指定为 a909502dd82ae41433e6f83886b00d4277a32a7b。 |
| -tpmandpin | 为操作系统驱动器添加受信任的平台模块（TPM）和个人标识号（PIN）保护程序。 你还可以使用 **-tp**作为此命令的缩写形式。 |
| -tpmandstartupkey | 添加操作系统驱动器的 TPM 和启动密钥保护程序。 你还可以使用 **-tsk**作为此命令的缩写形式。 |
| -tpmandpinandstartupkey | 为操作系统驱动器添加 TPM、PIN 和启动密钥保护程序。 你还可以使用 **-tpsk**作为此命令的缩写形式。 |
| -password | 添加数据驱动器的密码密钥保护程序。 你还可以使用 **-pw**作为此命令的缩写形式。 |
| -adaccountorgroup | 为卷添加基于安全标识符（SID）的标识保护程序。 你还可以使用 **-sid**作为此命令的缩写形式。 **重要提示：** 默认情况下，不能使用 WMI 或 manage-bde 远程添加 ADaccountorgroup 保护程序。 如果你的部署需要能够远程添加此保护程序，则必须启用约束委派。 |
| -computername | 指定正在使用 manage-bde 修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

#### <a name="additional--delete-parameters"></a>其他-删除参数

```
manage-bde -protectors -delete <drive> [-type {recoverypassword|externalkey|certificate|tpm|tpmandstartupkey|tpmandpin|tpmandpinandstartupkey|Password|Identity}]
[-id <keyprotectorID>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -type | 标识要删除的密钥保护程序。 你还可以使用 **-t**作为此命令的缩写形式。 |
| ms-fve-recoverypassword | 指定应删除任何恢复密码密钥保护程序。 |
| externalkey | 指定应删除与驱动器关联的任何外部密钥保护程序。 |
| 证书 (certificate) | 指定应删除与驱动器关联的任何证书密钥保护程序。 |
| tpm | 指定应删除与驱动器关联的任何仅 TPM 密钥保护程序。 |
| tpmandstartupkey | 指定应删除与驱动器关联的任何基于 TPM 和启动密钥保护程序的密钥保护程序。 |
| tpmandpin | 指定应删除与驱动器关联的任何基于 TPM 和 PIN 的密钥保护程序。 |
| tpmandpinandstartupkey | 指定应删除与驱动器关联的任何基于 TPM、PIN 和启动密钥保护程序的密钥保护程序。 |
| password | 指定应删除与驱动器关联的任何密码密钥保护程序。 |
| identity | 指定应删除与驱动器关联的任何标识密钥保护程序。 |
| -ID | 使用密钥标识符标识要删除的密钥保护程序。 此参数是 **-type**参数的替代选项。 |
| `<keyprotectorID>` | 标识要删除的驱动器上的单个密钥保护程序。 可以通过使用**manage-bde-保护程序-get**命令显示密钥保护程序 id。 |
| -computername | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

#### <a name="additional--disable-parameters"></a>其他-禁用参数

```
manage-bde -protectors -disable <drive> [-rebootcount <integer 0 - 15>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| rebootcount | 指定在重新启动 Windows 后，操作系统卷的保护已挂起，并将在**rebootcount**参数中指定的次数后恢复。 指定**0**则无限期挂起保护。 如果未指定此参数，则在重新启动 Windows 后，BitLocker 保护将自动恢复。 还可以使用 **-rc**作为此命令的缩写形式。 |
| -computername | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要将证书密钥保护程序（由证书文件标识）添加到驱动器 E，请键入：

```
manage-bde -protectors -add E: -certificate -cf c:\File Folder\Filename.cer
```

若要将**adaccountorgroup**密钥保护程序（由域和用户名标识）添加到驱动器 E，请键入：

```
manage-bde -protectors -add E: -sid DOMAIN\user
```

若要在计算机重新启动3次之前禁用保护，请键入：

```
manage-bde -protectors -disable C: -rc 3
```

若要在驱动器 C 上删除所有基于 TPM 和启动密钥的密钥保护程序，请键入：

```
manage-bde -protectors -delete C: -type tpmandstartupkey
```

若要将驱动器 C 的所有恢复信息备份到 AD DS，请键入：

```
manage-bde -protectors -adbackup C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
