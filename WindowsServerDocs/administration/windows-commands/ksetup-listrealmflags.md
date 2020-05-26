---
title: ksetup listrealmflags
description: Ksetup listrealmflags 命令的参考主题，其中列出了可由 ksetup 报告的可用领域标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5c5ebbee7f937733286e0354eca1cf5524459e86
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817717"
---
# <a name="ksetup-listrealmflags"></a>ksetup listrealmflags

列出**ksetup**可以报告的可用领域标志。

## <a name="syntax"></a>语法

```
ksetup /listrealmflags
```

### <a name="remarks"></a>备注

- 领域标志指定了不基于 Windows Server 操作系统的 Kerberos 领域的其他功能。 运行 Windows Server 的计算机可以使用 Kerberos 服务器来管理 Kerberos 领域中的身份验证，而不是使用运行 Windows Server 操作系统的域。 此条目将建立领域的功能，如下所示：

| Value | 领域标志 | 说明 |
| ----- | ---------- | ----------- |
| 0xF | 全部 | 设置所有领域标志。 |
| 0x00 | 无 | 未设置领域标志，并且未启用任何其他功能。 |
| 0x01 | sendaddress | 此 IP 地址将包含在票证授予票证中。 |
| 0x02 | tcpsupported | 此领域支持传输控制协议（TCP）和用户数据报协议（UDP）。 |
| 0x04 | delegate | 此领域中的每个人都受信任，可用于委派。 |
| 0x08 | ncsupported | 此领域支持名称规范化，这允许 DNS 和领域的命名标准。 |
| 0x80 | rc4 | 此领域支持 RC4 加密以启用跨领域信任，这允许使用 TLS。 |

- 领域标志存储在下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>` 。 默认情况下，注册表中不存在此项。 可以使用[ksetup addrealmflags 命令](ksetup-addrealmflags.md)填充注册表。

## <a name="examples"></a>示例

若要列出此计算机上的已知领域标志，请键入：

```
ksetup /listrealmflags
```

若要设置**ksetup**不知道的可用领域标志，请键入：

```
ksetup /setrealmflags CORP.CONTOSO.COM sendaddress tcpsupported delete ncsupported
```

**或**

```
ksetup /setrealmflags CORP.CONTOSO.COM 0xF
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup addrealmflags 命令](ksetup-addrealmflags.md)

- [ksetup setrealmflags 命令](ksetup-setrealmflags.md)

- [ksetup delrealmflags 命令](ksetup-delrealmflags.md)
