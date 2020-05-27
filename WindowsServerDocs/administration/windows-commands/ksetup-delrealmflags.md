---
title: ksetup delrealmflags
description: Ksetup delrealmflags 命令的参考主题，它删除指定领域中的领域标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 22053041-1eb4-47f5-bed9-3d5681bcde7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a8d983a00683fec0fa1bb9801caabe226a4ffeb9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817827"
---
# <a name="ksetup-delrealmflags"></a>ksetup delrealmflags

删除指定领域中的领域标志。

## <a name="syntax"></a>语法

```
ksetup /delrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或**领域 =** 列出。 |

#### <a name="remarks"></a>备注

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

- 可以通过查看**ksetup**或的输出来查看可用的和设置领域标志 `ksetup /dumpstate` 。

### <a name="examples"></a>示例

若要列出领域 CONTOSO 的可用领域标志，请键入：

```
ksetup /listrealmflags
```

若要删除集中当前的两个标志，请键入：

```
ksetup /delrealmflags CONTOSO ncsupported delegate
```

若要验证是否已删除领域标志，请键入， `ksetup` 然后查看输出，查找文本 "**领域标志 =**"。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup listrealmflags 命令](ksetup-listrealmflags.md)

- [ksetup setrealmflags 命令](ksetup-setrealmflags.md)

- [ksetup addrealmflags 命令](ksetup-addrealmflags.md)

- [ksetup dumpstate 命令](ksetup-dumpstate.md)
