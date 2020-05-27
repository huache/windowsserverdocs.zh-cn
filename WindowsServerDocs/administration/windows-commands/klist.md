---
title: klist
description: Klist 命令的参考主题，其中显示当前缓存的 Kerberos 票证的列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4689b4a9-1740-47dd-9240-02105efca428
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 58a3ae0ffc223710f62355180ba590ff6b34b188
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818137"
---
# <a name="klist"></a>klist

显示当前缓存的 Kerberos 票证的列表。

> [!IMPORTANT]
> 若要运行此命令的所有参数，您必须至少具有**域管理员**或同等身份。

## <a name="syntax"></a>语法

```
klist [-lh <logonID.highpart>] [-li <logonID.lowpart>] tickets | tgt | purge | sessions | kcd_cache | get | add_bind | query_bind | purge_bind
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -lh | 表示以十六进制表示的用户本地唯一标识符（LUID）的高部分。 如果两者**都不**存在 **–li** ，则该命令默认为当前已登录用户的 LUID。 |
| -li | 表示以十六进制表示的用户本地唯一标识符（LUID）的低部分。 如果两者**都不**存在 **–li** ，则该命令默认为当前已登录用户的 LUID。 |
| 赛 | 列出当前缓存的票证授予票证（Tgt）和指定的登录会话的服务票证。 这是默认选项。 |
| tgt | 显示初始 Kerberos TGT。 |
| 清空 | 允许您删除指定登录会话的所有票证。 |
| 会话 | 显示此计算机上的登录会话的列表。 |
| kcd_cache | 显示 Kerberos 约束委派缓存信息。 |
| get | 允许您向由服务主体名称（SPN）指定的目标计算机请求票证。 |
| add_bind | 允许你指定用于 Kerberos 身份验证的首选域控制器。 |
| query_bind | 显示 Kerberos 已联系的每个域的缓存首选域控制器的列表。 |
| purge_bind | 为指定的域删除缓存的首选域控制器。 |
| kdcoptions | 显示 RFC 4120 中指定的密钥发行中心（KDC）选项。 |
| /? | 显示此命令的帮助。 |

#### <a name="remarks"></a>备注

- 如果未提供任何参数， **klist**将检索当前已登录用户的所有票证。

- 参数显示以下信息：

  - "**票证**"-列出自登录后对其进行身份验证的当前已缓存服务的票证。 显示所有缓存票证的以下属性：

    - **LogonID：** LUID。

    - **客户端：** 客户端名称与客户端域名的串联。

    - **服务器：** 服务名称和服务的域名的串联。

    - **KerbTicket 加密类型：** 用于加密 Kerberos 票证的加密类型。

    - **票证标志：** Kerberos 票证标志。

    - **开始时间：** 票证有效的时间。

    - **结束时间：** 票证不再有效的时间。 当票证过期时，它无法再用于向服务进行身份验证或用于续订。

    - **续订时间：** 需要新的初始身份验证的时间。

    - **会话密钥类型：** 用于会话密钥的加密算法。

  - **tgt** -列出初始 Kerberos tgt 以及当前缓存的票证的以下属性：

    - **LogonID：** 在十六进制中标识。

    - **ServiceName：** krbtgt

    - **TargetName `<SPN>` ：** krbtgt

    - **DomainName：** 发出 TGT 的域的名称。

    - **TargetDomainName：** 向其颁发 TGT 的域。

    - **AltTargetDomainName：** 向其颁发 TGT 的域。

    - **票证标志：** Address 和 target 操作和类型。

    - **会话密钥：** 密钥长度和加密算法。

    - **StartTime：** 请求票证的本地计算机时间。

    - **EndTime：** 票证不再有效的时间。 当票证过期时，它无法再用于向服务进行身份验证。

    - **RenewUntil：** 票证续订截止时间。

    - **TimeSkew：** 与密钥发行中心（KDC）的时间差。

    - **EncodedTicket：** 编码的票证。

  - **清除**-允许删除特定的票证。 清除票证会销毁已缓存的所有票证，因此请谨慎使用此属性。 它可能会阻止你无法对资源进行身份验证。 如果发生这种情况，则必须注销并重新登录。

    - **LogonID：** 在十六进制中标识。

  - **会话**-允许列出和显示此计算机上所有登录会话的信息。

    - **LogonID：** 如指定，则只按给定的值显示登录会话。 如果未指定，则显示此计算机上的所有登录会话。

  - **kcd_cache** -允许显示 Kerberos 约束委派缓存信息。

    - **LogonID：** 如指定，则按给定的值显示登录会话的缓存信息。 如果未指定，则显示当前用户的登录会话的缓存信息。

  - **get** -允许向 SPN 指定的目标请求票证。

    - **LogonID：** 如果已指定，则通过使用登录会话通过给定的值请求票证。 如果未指定，则使用当前用户的登录会话请求票证。

    - **kdcoptions：** 请求具有给定 KDC 选项的票证

  - **add_bind** -允许你指定用于 Kerberos 身份验证的首选域控制器。

  - **query_bind** -允许显示域的缓存首选域控制器。

  - **purge_bind** -允许删除域的缓存首选域控制器。

  - **kdcoptions** -有关最新的选项列表及其说明，请参阅[RFC 4120](http://www.ietf.org/rfc/rfc4120.txt)。

### <a name="examples"></a>示例

若要查询 Kerberos 票证缓存以确定是否缺少任何票证、目标服务器或帐户是否出错，或者如果由于事件 ID 27 错误而不支持加密类型，请键入：

```
klist
```

```
klist –li 0x3e7
```

若要了解计算机上为登录会话缓存的每个票证授予票证的详细信息，请键入：

```
klist tgt
```

若要清除 Kerberos 票证缓存，注销，然后重新登录，请键入：

```
klist purge
```

```
klist purge –li 0x3e7
```

若要诊断登录会话并查找用户或服务的 logonID，请键入：

```
klist sessions
```

若要诊断 Kerberos 约束委派失败并查找遇到的最后一个错误，请键入：

```
klist kcd_cache
```

若要诊断用户或服务是否可以获取服务器的票证，或若要请求特定 SPN 的票证，请键入：

```
klist get host/%computername%
```

若要诊断域控制器间的复制问题，通常需要客户端计算机以特定的域控制器为目标。 若要将客户端计算机定位到特定的域控制器，请键入：

```
klist add_bind CONTOSO KDC.CONTOSO.COM
```

```
klist add_bind CONTOSO.COM KDC.CONTOSO.COM
```

若要查询此计算机最近连接的域控制器，请键入：

```
klist query_bind
```

若要重新发现域控制器，或要在创建新的域控制器绑定之前刷新缓存 `klist add_bind` ，请键入：

```
klist purge_bind
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)