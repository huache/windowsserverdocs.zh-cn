---
title: ksetup listrealmflags
description: Ksetup listrealmflags 命令的参考文章，其中列出了可通过 ksetup 报告的可用领域标志。
ms.topic: reference
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ddbc7f2421fc9c4acfcb38d0e83776f550908e28
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640023"
---
# <a name="ksetup-listrealmflags"></a>ksetup listrealmflags

列出 **ksetup**可以报告的可用领域标志。

## <a name="syntax"></a>语法

```
ksetup /listrealmflags
```

### <a name="remarks"></a>备注

- 领域标志指定了不基于 Windows Server 操作系统的 Kerberos 领域的其他功能。 运行 Windows Server 的计算机可以使用 Kerberos 服务器来管理 Kerberos 领域中的身份验证，而不是使用运行 Windows Server 操作系统的域。 此条目将建立领域的功能，如下所示：

| “值” | 领域标志 | 说明 |
| ----- | ---------- | ----------- |
| 0xF | All | 设置所有领域标志。 |
| 0x00 | 无 | 未设置领域标志，并且未启用任何其他功能。 |
| 0x01 | sendaddress | 此 IP 地址将包含在票证授予票证中。 |
| 0x02 | tcpsupported | 传输控制协议 (TCP) 和用户数据报协议 (UDP) 在此领域中受支持。 |
| 0x04 | delegate | 此领域中的每个人都受信任，可用于委派。 |
| 0x08 | ncsupported | 此领域支持名称规范化，这允许 DNS 和领域的命名标准。 |
| 0x80 | rc4 | 此领域支持 RC4 加密以启用跨领域信任，这允许使用 TLS。 |

- 领域标志存储在下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>` 。 默认情况下，注册表中不存在此项。 可以使用 [ksetup addrealmflags 命令](ksetup-addrealmflags.md) 填充注册表。

## <a name="examples"></a>示例

若要列出此计算机上的已知领域标志，请键入：

```
ksetup /listrealmflags
```

若要设置 **ksetup** 不知道的可用领域标志，请键入：

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
