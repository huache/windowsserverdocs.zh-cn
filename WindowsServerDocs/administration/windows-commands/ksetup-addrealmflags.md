---
title: ksetup addrealmflags
description: Ksetup addrealmflags 命令的参考文章，可将其他领域标志添加到指定领域。
ms.topic: reference
ms.assetid: 80ca1e16-8871-494b-b9be-6bc9d63de860
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 44d03abea67011e7ef5544def8cb26655b4b41d1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639723"
---
# <a name="ksetup-addrealmflags"></a>ksetup addrealmflags

将其他领域标志添加到指定领域。

## <a name="syntax"></a>语法

```
ksetup /addrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM。 |

#### <a name="remarks"></a>备注

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

- 领域标志存储在下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>` 。 默认情况下，注册表中不存在此项。 可以使用 [ksetup addrealmflags](ksetup-addrealmflags.md) 命令填充注册表。

- 可以通过查看 **ksetup** 或的输出来查看可用的和设置领域标志 `ksetup /dumpstate` 。

### <a name="examples"></a>示例

若要列出领域 CONTOSO 的可用领域标志，请键入：

```
ksetup /listrealmflags
```

若要将两个标志设置为 CONTOSO 领域，请键入：

```
ksetup /setrealmflags CONTOSO ncsupported delegate
```

若要添加一个当前不在该集中的标记，请键入：

```
ksetup /addrealmflags CONTOSO SendAddress
```

若要验证是否已设置领域标志，请键入， `ksetup` 然后查看输出，查找文本 " **领域标志 =**"。 如果看不到文本，则表示尚未设置该标志。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup listrealmflags 命令](ksetup-listrealmflags.md)

- [ksetup setrealmflags 命令](ksetup-setrealmflags.md)

- [ksetup delrealmflags 命令](ksetup-delrealmflags.md)

- [ksetup dumpstate 命令](ksetup-dumpstate.md)
